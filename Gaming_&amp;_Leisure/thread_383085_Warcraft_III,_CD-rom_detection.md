---
title: "Warcraft III, CD-rom detection"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by Chake99 on 2007-03-12
I'm trying to get Warcraft III going. I got the install to succeed, but now attempting to launch the game returns >  Please make sure your Warcraft III disc is in your CD-ROM drive, and then click on 'retry'. 

I've looked at [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177) and my cd-rom drive I believe is properly configured (d: , set to cd-rom). As for software breaking the secuROM protection: 

> Linux vanilla x86 kernel: 2.6.9, 2.6.10
Linux vanilla x86-64 kernel: 2.6.9-2.6.15
Linux kernel versions less that 2.6
Wine compiled with GCC 4.0.0-4.0.2
Native msvcrt.dll
Nvidia video driver compiled against mismatched X11 header files
Fedora core 6 modified linux kernel, unless updated to 2.6.18-1.2784.fc6 or later 

Kernel wise I know I'm fine. My GCC version however is 4.1.2 according to the man page (is that really the proper place to check?) so that could be my problem. I installed wine from automatix; which I suppose compiled it for me. 

How would I get wine to work with warcraft III?

(would it be some wine uninstall, compile wine sources with old version of gcc wizardry? How?)

EDIT: stupid me 4.1.2 is higher than 4.0.2

Guess I'll try a nocd crack.

---

### Post by Iarwain ben-adar on 2007-03-13
Why don't you try with a no-cd crack?

gamecopyworld.com has alot of them :D


TO FORUM ADMIN: if the mentioning of this site is not allowed, please delete it.


Iarwain

---

### Post by beezkneez2005 on 2007-03-13
from [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

> Problems With "Please Insert Disc"

If you have followed *all* the proceeding instructions and you are having problems with the game asking for the disc, please contact me. Wine supports SecuRom fully. So if it doesn't work, it is very unusual, and more often it doesn't mean that you are having a real copy protection problem, but there is something wrong with your setup. It's also entirely possible to get the error message to insert the game disc, and have nothing to do with copy protection, when you do have it setup correctly. When making a report on this, please include your Wine version, Linux kernel version and targetted architechure, GCC version, Wine build options, video card driver name and provider, the listing of ~/.wine/dosdevices, and /etc/fstab.

---

