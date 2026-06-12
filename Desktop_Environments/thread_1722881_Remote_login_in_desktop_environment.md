---
title: "Remote login in desktop environment"
date: 2011-04-06
forum: Desktop Environments
---

### Post by Sidrabs on 2011-04-06
Hello,

I have my work PC in the office, and time to time I access it via TeamViewer from home. I have access to it also via ssh, over the VPN connection.

I have problems with this setup, when for some reason the work PC must be rebooted (or it just happened by itself - power failure). The Ubuntu gets to the login screen and that's it. I can not access it remotely because the TeamViewer application is not started on that PC yet.

I'd like to know, if there is a way how I can access my work PC over the VPN connection - open SSH session, and write some commands, to log in that desktop environment user, and launch the TeamViewer application. Ie, if someone would be looking on the screen at that moment, she would see that login screen disappears, desktop environment is loaded, and the TeamViewer app is started.

If that's not possible, then, I guess, I'll have resort to some alternative remote access tool (ie, VNC) what could be loaded before the Ubuntu login screen is shown. Then I could access it over the VPN connection, using appropriate client.

---

### Post by Krytarik on 2011-04-06
Check out both of these guides about how to handle the login screen via VNC:
[http://ubuntuforums.org/showthread.php?p=10172825](http://ubuntuforums.org/showthread.php?p=10172825)
[http://ubuntuforums.org/showthread.php?p=10172825#post10172825](http://ubuntuforums.org/showthread.php?p=10172825#post10172825)

Note: I don't know if either of these setups works.

Greetings.

---

