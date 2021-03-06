# 4d-plugin-system-notification
Register callback method for display sleep/wake, system sleep/wake, quit (mac) and logoff (windows).

##Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|🆗|🆗|🆗|🆗|

##Examples

```
  //install event handler method
  //its signature should be C_LONGINT($1)

$success:=SN Set method ("SYSTEM_EVENT")

  //when the user logs off, or the system decideds to reboot

  //on Mac;
  //all applications are asked to quit; you should handle the "On Before Quit" event.
  //the system waits 60 secs for your app to quit.

  //on Windows;
  //all applications are asked if it is OK to end the session; you should handle the "On Before Machine Power Off" event.
  //the system displays "programs still running" screen and waits for your app to quit.

  //platform considerations:
  //on Mac, there is not differentiation between a simple request to quit and a request to quit prior to a system reboot.
  //on Mac, if your app does not quit within 60 seconds, the reboot is cancelled.

  //to quickly test screen sleep notifications:
  //Mac: control+shift+power
  //Windows: http://www.itworld.com/article/2699995/consumerization/how-to-quickly-put-your-monitor-to-sleep.html
  ```
  
* Callback method

```
C_LONGINT($1)

Case of 
: ($1=SN On After Machine Wake)
ALERT("On After Machine Wake")
: ($1=SN On Before Screen Sleep)
ALERT("On Before Screen Sleep")
: ($1=SN On After Screen Wake)
ALERT("On After Screen Wake")
: ($1=SN On Before Machine Sleep)
ALERT("On Before Machine Sleep")
: ($1=SN On Before Machine Power Off)
ALERT("On Before Machine Power Off")
: ($1=SN On Before Quit)
ALERT("On Before Quit")
End case 
```
