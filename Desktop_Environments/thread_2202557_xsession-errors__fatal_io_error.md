---
title: "xsession-errors  fatal io error"
date: 2014-01-29
forum: Desktop Environments
---

### Post by mindbox on 2014-01-29
```
#grep -i error /home/dan/.xsession-errors.old
Window manager warning: Log level 16: gnome-shell: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(cinnamon-fallback-mount-helper:3933): Gdk-WARNING **: cinnamon-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
clipit: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(gnome-shell-calendar-server:4011): Gdk-WARNING **: gnome-shell-calendar-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(nm-applet:3937): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
shutter: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(cinnamon-screensaver:4079): Gdk-WARNING **: cinnamon-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
```

Hello, I have a lot of trouble with slow login and I've been poking around looking for some clues as to why. I found this error in xsesssion-errors. Can anyon help me with it? 

I'm running 12.04 on intel i7, intell HD 4000, lenovo G780,

Thanks

---

### Post by tgalati4 on 2014-01-30
Any errors in /var/log/Xorg.0.log?  It looks like a graphics chip problem.  I presume that this system was working OK previously?  How long have you been running 12.04 on this system?

Set up another computer and log in via ssh so that if your screen freezes, you can still see what is going on from another terminal.  Run a few cycles of *memtest* to make sure your RAM is working OK.

If it is a hardware error, you can get a lot of misleading log errors that will have you pull your hair out chasing them.  So keep an open mind when troubleshooting.

---

### Post by mindbox on 2014-01-30
Thanks for the reply.

 I have no errors (EE) in /var/log/Xorg.0.log. The system worked after I installed it. However, being new to linux I've installed many other window managers and programs. I don't know if the problem is related to this or not. 

I don't know how to use ssh and unfortunatly I don't have internet at home. I can log into another terminal via ctrl+alt+F1. And I have checked to see if any programs suck up the CPU via top. I've noticed gzip and init at times take a lot of cpu but that is about it. 

I have my system tripple-booting windows 8, and a small partition running ubuntu 13.1 which logs-in just fine 5-10 seconds. I have slow login for all window managers but gnome has the strange problem of not loading my settings for icons and background. It likes to revert to the default options. Again, I don't know if any of this is related. Is there any chance that 12.04.4 or 14.04 (when it comes out) would fix my problems?

---

