---
title: "XServer broken after trying to get XGL working"
date: 2006-12-09
forum: Desktop Environments
---

### Post by garethppls on 2006-12-09
Hi I tried to install the xserver-glx and all on Kubuntu following the guide for Ubuntu at the Beryl site (I forget the link) but now it crashes at the startup and as it should be loading the KDE login it goes to a console. It doesn't leave any error message but I tried to install GLX and all beforehand. I would like to get the system back to its previous form as I had loads of MP3's and a good setup going and I hate Windows. I solo boot this one one of my PC's in the house.

If anyone could help I'd be most grateful,
Gareth

---

### Post by adaptr on 2006-12-09
There are several things you should mention before anyone can give you meaningful answers:

- How,exactly, did you install Beryl ?
Note that XGL by itself doesn't break anything - it's only when trying to use Beryl or compiz that stuff goes wrong.

- What kind of video hardware do you have - nVidia, ATI, or what ?

- what are the messages displayed when you run "startx" from a console ?

These messages are saved in a log file called /var/log/xorg.0.log

---

### Post by garethppls on 2006-12-10
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL)

I followed that guide, and secondly after I removed xserver-xgl it went back to the working form it was in before i started the tutorial. I'd like to try have the effects on though I have a pretty good PC.
I'm using a Nvidia Geforce 6200 PCI-e

---

