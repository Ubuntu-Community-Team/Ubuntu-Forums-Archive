---
title: "Can't seem to get my AMD GPU to be used with open source drivers"
date: 2015-02-02
forum: Gaming &amp; Leisure
---

### Post by Shinsekai_Yori on 2015-02-02
I'm on Ubuntu 14.10 with kernel 3.16 on a Lenovo Y40, which has a Haswell iGPU and a Radeon R9 M275X. With Catalyst I get good  performance in games, but scrolling performance is horrid, HTML5 videos  have screen tearing, my laptop runs ~20C hotter, battery life tanks, and  I've had several freezes that required a restart. The open source  drivers are preferable for almost everything, the exception being gaming  since performance is abysmal.

 I can't seem to get my AMD card to ever work in the open source  drivers. In Additional Drivers it says I'm using the AMD/ATI display  driver wrapper, but in Steam and the commands glxgears -info and glxinfo | grep "OpenGL  renderer" it says I have Haswell graphics. xrandr --listproviders does  list the Radeon card (twice, as provider 1 and 2), but xrandr  --setprovideroffloadsink 1 0 doesn't seem to do a thing. I've tried  starting glxinfo, glxgear, and Steam with DRI_PRIME=1, but that also doesn't  do anything.

---

### Post by QIII on 2015-02-02
Using the Catalyst Control Center, are you able to switch from integrated to the AMD adapter?

The selection is not dynamic as in Windows.  You have to reboot.

---

### Post by Shinsekai_Yori on 2015-02-02
Last time I tried, no. The choice wouldn't stick and it'd go back to using the AMD card.

---

