---
title: "The dreaded hang on startup - FIXED"
date: 2005-06-16
forum: Desktop Environments
---

### Post by pauls101 on 2005-06-16
The problem is a total system freeze (except that the mouse still moves) shortly after booting into KDE or Gnome. In my case, when I could tell, it usually followed opening a window (KDE) or resizing one (Gnome.)

The fix turned out to be installing the latest Nvidia drivers (I have a GeForce2.) This driver appears as "nvidia" in xorg.conf rather than the older "nv".

Complete instructions using apt-get are at [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver).  It'll ask for your ubuntu CD, and does need to be done from a command line (boot normally and immediately use Ctrl-Alt-Backspace before it freezes: easier than Recovery Mode.)

This is a great system now that I can use it!


The problem seems to be widespread: I reproduced it with Mepis and got a lot of suggestions off Gentoo's forums. W/ the new drivers I reverted all my experimental changes to xorg.conf and the BIOS, and now everything just works.

---

