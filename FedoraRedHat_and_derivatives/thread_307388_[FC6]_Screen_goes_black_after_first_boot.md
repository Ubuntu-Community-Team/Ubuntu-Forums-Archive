---
title: "[FC6] Screen goes black after first boot"
date: 2006-11-26
forum: Fedora/RedHat and derivatives
---

### Post by Arandil on 2006-11-26
Since I felt kind of frustrated at the way Opensuse tripped over AIXGL, I decided to give Fedora a try. Installation went painless, but soon afterwards a problem rose up.

After the installation I was asked to reboot in order to complete the installation. The "first time"-wizard popped up, filled in all the details, and then... nothing. I saw a glimpse of a login prompt after the wizard, but it was too short to log in. Nothing more happened after that, the screen remains solid black.

What I tried so far:

* booted in runlevel 3, open the log in /var/log/Xorg.0.log, but no EE's were present
* booted again in runlevel 3, tried system-config-display --reconfig, that seems to do something, however the screen goes black again
* Output of /etc/X11/xorg.conf file shows no "monitor"-section, only Serverlayout, Inputdevice, Device and screen. Could this be a problem?


My graphics card is a Radeon 9200. I understand that it should work out of the box, even wit compiz (which is one of the reasons to choose for FC6). Could anyone point in the right direction?

---

### Post by jinx099 on 2006-12-05
I had the exact same problem.  The problem is the video driver.  It defaulted to vesa for me, which should work, but didnt apparently.  Just boot to runlevel 3 and change the vesa driver to ati or radeon.

---

### Post by NImacTry2 on 2007-07-28
To join the club... I am experiencing the same problem. Running Ubuntu on Notebook Toshiba A135 S2386 with 2Gb RAM. Everything basically works perfect just this is the thing I do not like. I do not have much need to change users anyway, but just want this to work!

By the way, I am pretty new in Ubuntu (using it for a few days) and for now I found it awesome! Just two more things to make work Logitech Web Camera and TrendNet 105UB bluetooth device. Already found something for those devices but hope will manage to make it work...

Thank you in advance,
Djordje

---

### Post by Dark Seraphim on 2007-07-28
I had the same problem to and I have an intel graphics card I pressed ctrl+alt+backspace a coupke times and it finally showed altough I still had the problem later on when I restarted. if it wasnt for that I might actually use it and of course some other things.

---

### Post by angryfirelord on 2007-07-29
Run system-config-display. Select the Hardware tab and configure video card. Select radeon. Then. configure your monitor and pick the best resolution for it.

---

