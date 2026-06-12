---
title: "Resolution Problems.."
date: 2005-03-20
forum: Desktop Environments
---

### Post by MicroChris on 2005-03-20
Would it be possible for someone to post their unaltered xorg.conf file? One without any type of drivers loaded or anything.. I want to see what the default resolution and Hz is... 

It was 1600x1200 before, but now it won't work and Im getting a shitty res thats making my head split in two and its making me feel dizzy as shit.. 


So, please, help. 

Thanks
Chris

---

### Post by MicroChris on 2005-03-20
I can get to 1600x1200, but only with 60Hz or 65Hz.. Im guessing the default is more like 80-85Hz.

Im running a Radeon 7500 (which means no fgl drivers for meee).

Thanks!
Chris

---

### Post by cdhotfire on 2005-03-20
shutdown gnome
```
sudo /etc/init.d/gdm stop
```
and run the reconfigure
```
sudo dpkg-reconfigure xserver-xorg
```
should let you choose.

---

### Post by MicroChris on 2005-03-20
Alrighty, thanks a bunch!

-Chris

---

### Post by gnutux on 2005-03-20
it all depends on your monitor. If it supports more than 60-70 Hz, then set it to a bigger frequency. For most of monitors out there, it's 60-70 Hz only.

gnutux

---

### Post by MicroChris on 2005-03-20
Thanks cdhotfire, it did the trick!


-Chris

---

### Post by cdhotfire on 2005-03-20
no problem dude. :D

---

