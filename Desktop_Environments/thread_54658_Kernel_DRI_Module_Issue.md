---
title: "Kernel DRI Module Issue"
date: 2005-08-05
forum: Desktop Environments
---

### Post by ph8 on 2005-08-05
Hey all, new problem ,new post! I think this error is stopped my gfx card working - running Ubuntu latest-stable (as of last week)

Regards, Henri

(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *


I can't find any DRI package though.. any advice?

---

### Post by JLTB on 2005-08-06
Hi,

DRI (the direct redering interface) is something that your graphics card drivers have to use to do accelerated stuff in linux.  You don't need to "install DRI" per se.  Rather you need working graphics drivers to take advantage of it.

I've had that same error message several times and it basically means that linux couldn't load your graphics drivers for some reason or another.

You can use the command glxinfo to check to see the status of your graphics card (it will probably say something like "Direct redering: No" if you are getting errors like before).

Make sure you followed the installation guide for your graphics drivers to the letter and generally its not a good idea to try to install updated drivers (ie: from ati or nvidia site) until you get the ubuntu ones working properly.

---

