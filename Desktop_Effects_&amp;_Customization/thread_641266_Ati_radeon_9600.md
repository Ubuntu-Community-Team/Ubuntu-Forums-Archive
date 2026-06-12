---
title: "Ati radeon 9600"
date: 2007-12-15
forum: Desktop Effects &amp; Customization
---

### Post by xodroolis on 2007-12-15
I am tottaly new to Ubuntu 
i have ubuntu 7.10 on an AMD athlon xp 2400+
and ATI radeon 9600 pro

i followed this guide** [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)**
but in the end i get

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

instead of 
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6650 (8.40.4)

I cant change the desktop effects further than "none"
and i get a message desktop effects could not be enabled

Some help please :(

---

### Post by erfahren on 2007-12-15
first off here.... that guide actually contains two guides. The "Method 1" just has you install the driver from the Ubuntu repos, and "Method 2" is to install the newest version from ATI. Which one did you do?

side note to old Windows users... with Linux, installing the most recent version of a driver directly from the vendor isn't always necessary (or recommended).

---

### Post by _angel__ on 2007-12-15
My video card is 9800,and i was using this guide when I install the driver
[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)
Everything went well and working great.

---

### Post by xodroolis on 2007-12-15
> **erfahren said:**
> first off here.... that guide actually contains two guides. The "Method 1" just has you install the driver from the Ubuntu repos, and "Method 2" is to install the newest version from ATI. Which one did you do?

side note to old Windows users... with Linux, installing the most recent version of a driver directly from the vendor isn't always necessary (or recommended).

I followed the 1st guide

---

### Post by erfahren on 2007-12-15
ok, well you shouldn't even have to do that. If you go to System > Administration > Restricted Drivers Manager and enable the driver it does the downloading and installing that needs done. (Sry, but I have to ask, did you go to the Restricted Drivers Manager and try enabling it? If so did you get any errors?)

Did you get any errors when installing it by the directions on that wiki? (One other simple, yet common problem is the "restricted" repository isn't enabled in the Software Sources.)

---

### Post by xodroolis on 2007-12-15
thanks for trying helping me
For now i will just use the The Radeon open-source driver (ati)
and if i see that i need the closed-source driver from ati.
After all i am totaly new to ubuntu and i want to watch it run for a while
Thanks anyway

---

