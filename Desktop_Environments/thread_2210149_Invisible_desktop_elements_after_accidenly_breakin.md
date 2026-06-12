---
title: "Invisible desktop elements after accidenly breaking XOrg ati drivers"
date: 2014-03-09
forum: Desktop Environments
---

### Post by Mikey_Kaza on 2014-03-09
Ubuntu 1310 running with a RAEDON HD mobility 5450 card. I had successfully, before this problem, switched between the opensource XOrg drivers, and the propritary ones. Along the way I was in ccsm and accidenly disabled opengl while on the XOrg drivers. This caused the unity option to get taken off by default as well and things got weird. 

First, a brief error pop up, followed a few miliseconds afterwards by a crash. 

Now when I try to launch ubuntu with XOrg drivers, im greeted to an invisible login in screen, with an invisible mouse pointer. After login, only the top bar with indicators, and wallpaper, appears. I connect to internet, cpu monitor works fine but my terminal keyboard shortcut will not work and the left launcher bar is does not appear. I get stuck completely and have to reboot from tty1 or something. 

To get to this place from where I started I did the following to try and fix this:
repair broken packages
reinstall proprietary drivers
reinstall XOrg drivers
compiz --replace
restored a recent /etc/X11/conf backup

Booting into recovery move, into low graphics mode allows me to change back to propreitary drivers, reboot and everything works fine. 

My main goal is to get a terminal to summon in my XOrg state. Secondary concern is to figure out what's causing this. Any insight would be appreciated.

---

