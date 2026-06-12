---
title: "Getting wacom tablet to work with two screens"
date: 2008-06-20
forum: Desktop Environments
---

### Post by Sarasvati on 2008-06-20
I have two screens which work with the built in touchpad, but my tablet only works on the left half of my left screen and the right half of my right screen. Other wise the tablet works as it is supposed to work, it moves without having to touch the pad. I have added the necessary lines to /etc/X11/xorg.conf to get the tablet to work. I also configured the Monitor using nevidia-settings. I want the tablet to operate on one screen at a time and to be able to use buttons to swap between the screens.

So can anybody help me with this? 

Ps: I am no superuser, and my wonderfull Support is leaving the country so I am trying on my own :)

---

### Post by vinx on 2008-12-22
You're not alone... 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483494](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483494)
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/298707](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/298707)

I heard you could fix it by setting a option in xorg.conf
Option "KeepShape" "on"
Maybe someone else can help, or you could search the web.

You need root-access. Just ask around on this forum how to edit and BACKUP xorg.conf exactly, before you kill your pc:
> sudo gedit /etc/X11/xorg.conf

---

