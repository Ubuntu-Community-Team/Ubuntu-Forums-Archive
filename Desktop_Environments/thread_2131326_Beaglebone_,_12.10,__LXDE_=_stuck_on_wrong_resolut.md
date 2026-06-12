---
title: "Beaglebone , 12.10,  LXDE = stuck on wrong resolution"
date: 2013-04-01
forum: Desktop Environments
---

### Post by digiteltlc on 2013-04-01
Hi All
New to this forum

Just installed Quantal 12.10 armhf on a Beaglebone (not BeagleBoard) factory-equipped with an Ampire AM640480G2 touch monitor supporting 640x480 resolution

( [http://elinux.org/BeagleBoardUbuntu](http://elinux.org/BeagleBoardUbuntu) )

After LXDE was installed, graphic desktop environment starts at 800x480 resolution and there is no other resolution to choose, 
Pratically, the desktop environment is clearly displayed, but I can see only the 640x480 area allowed by display hardware 

All I tried to change resolution manually ( [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and many forums ) failed :  xrandr --output <> --mode<> = xrandr: configure crt 0 failed

Probably something during boot tells the system that a 800x400 monitor is present instaed the right 640x480

 
Any idea on what to try ???

Thank you very much

---

### Post by crvella on 2013-06-27
try looking in /boot/uboot/uEnv.txt

There is a section in there which you can set your display resolution

---

