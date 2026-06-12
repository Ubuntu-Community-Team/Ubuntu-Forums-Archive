---
title: "fglrx remove caused fail to login to graphical enviroment"
date: 2011-06-07
forum: Desktop Environments
---

### Post by dancer_69 on 2011-06-07
I've recently installed gnome3 on natty from ppa and I had graphic flickering problems and glitches. I found that the problem is with fglrx driver, so I remove it.
But after I rebooted gdm don't start and I cannot login to graphical enviorment.
Any help please???

**EDIT**
By booting in recovery mode and reconfigure xserver I was able to login to gnome3 and all seem normal, but after a reboot I get a black screen with blink cursor..

---

### Post by dancer_69 on 2011-06-07
Solved by purge fglrx and xserver ati. But after that I fallback to the normal gnome 2 look.

---

