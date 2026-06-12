---
title: "i740 problem"
date: 2005-09-30
forum: Desktop Environments
---

### Post by damnhatesyou on 2005-09-30
I Install a Ubuntu on to a Celeron 400. and when Gnome shows up it show the resolution of 640*480 refresh rate was stuck @ 60hz in "SYSTEM > PREFERENCES > SCREEN RESOLUTION". it is connected to a 17" Lite-on Monitor(A1770). i tried running xorgconf but it broke Xorg. and "dpkg-reconfigure xserver-xorg" did nothing too.

---

### Post by mlomker on 2005-09-30
You're going to have to attach your /etc/X11/xorg.conf file and the /var/log/Xorg.0.log file for anyone to take a guess.

---

### Post by poontang on 2005-10-01
[QUOTE=damnhatesyou]I Install a Ubuntu on to a Celeron 400. and when Gnome shows up it show the resolution of 640*480 refresh rate was stuck @ 60hz in "SYSTEM > PREFERENCES > SCREEN RESOLUTION". it is connected to a 17" Lite-on Monitor(A1770). i tried running xorgconf but it broke Xorg. and "dpkg-reconfigure xserver-xorg" did nothing too.[/QUOTE]

u need to add the HorizSync and VertRefresh ranges for your monitor:

[http://www.linuxquestions.org/questions/history/341238](http://www.linuxquestions.org/questions/history/341238)

and it should go fine

---

