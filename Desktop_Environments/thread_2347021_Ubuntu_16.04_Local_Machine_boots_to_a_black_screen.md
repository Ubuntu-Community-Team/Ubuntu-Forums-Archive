---
title: "Ubuntu 16.04 Local Machine boots to a black screen instead of login page"
date: 2016-12-20
forum: Desktop Environments
---

### Post by trinsic1 on 2016-12-20
I am trying to get some form of remote desktop working, so I followed the instructions on [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04) to setup a vnc server. Im able to log in, but I get some errors while its building the desktop display:       

```
 An error window pops up right when the startxfce4 command is put in saying: "Unable to contact settings server" 
//bin/dbus-launch terminated abnormally with the following error: EOF in dbus-launch reading address from bus daemon

and followed by a second error message that is:
"unable to load a failsafe session"
Unable to determine failsafe session name. Possible causes:xfconfd isn't running (D-Bus setup problem); environment variable $XDG_CONFIG_DIRS is set incorrectly (must include "/etc"), or xfce4-session is installed incorrectly.
   
```   

The error messages keep popping up and wont go away if I close them and the desktop does not respond when I try to open applications.

The other and most important matter is now when I restart my ubuntu machine I can hear the gnome welcome screen sound, but all I get on the screen is the last command that the startup executed.   The login screen does not appear and cannot login, but can login from ALT-F1 So some how the login screen GUI is not working. Any help would be appreciated, I dont know what to google for since I dont know what system is the culprit.

---

### Post by howefield on 2016-12-21
> **trinsic1 said:**
> I am trying to get some form of remote desktop working...

I'd suggest having a look at X2GO :)

[http://wiki.x2go.org/doku.php](http://wiki.x2go.org/doku.php)

---

### Post by trinsic1 on 2016-12-21
Thanks but im not looking to change remote desktop right now. In fact I just want to use Vino if I could because I want to be able to log into the current logged in desktop and not create a new desktop session. I cant seem to get vino working.

The most important thing is to get my gui login screen back so I dont have to login via command line.

---

