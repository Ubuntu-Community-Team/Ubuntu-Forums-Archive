---
title: "Remove application from start-up"
date: 2011-01-13
forum: Desktop Environments
---

### Post by lachmaca on 2011-01-13
Hi, 

I am running Unbuntu 10.10 on a HTPC, and also XBMC. With some effort it worked ok, sounds, remote etc.

Via systems>preferences I managed to add XBMC to the startup. It now starts when I start the PC. However it sort-of hijacks the PC, so the WiFi does not start among other things. Also I am no longer able to log into the desktop, so I am not able to emove XBMC from the start-up of the computer. If I exit XBMC I get to the log-in screen for the desktop, but when I log in it starts XBMC directly.

How can I remove it via the terminal? I cannot find a .config directory, any autostart, any .xsession, .xinitrc or anything else that looks like startup-script.

How can I get access to my desktop again?

---

### Post by Elfy on 2011-01-13
Found a few possibly helpful items.

First though can you login to a normal gnome if you choose at login - look at the bottom of login screen. 

If not and you can access a terminal in xbmc then the command to run the session properties is 

```
gnome-session-properties
```

[HOWTO: Disable or Enable Gnome Session Startup Applications from Command Line ]("http://ubuntuforums.org/showthread.php?t=1067101")

[http://ubuntuforums.org/showthread.php?t=347089](http://ubuntuforums.org/showthread.php?t=347089)

---

### Post by lachmaca on 2011-01-14
Thanks, through the referenced HOWTO I got enough of a pointer as to where I should start looking, and so i could regain my dektop and get may system back up again. Many thanks!

---

### Post by garyw32 on 2011-09-14
What you need to do is exit out of XBMC to the Ubuntu login screen.  Press return and in the bottom bar you will be able to change the session mode back to Ubuntu. 

However I haven't worked out how to get XBMC to autostart again.

Running 11.04.

---

