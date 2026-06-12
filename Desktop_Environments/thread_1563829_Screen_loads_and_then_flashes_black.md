---
title: "Screen loads and then flashes black"
date: 2010-08-29
forum: Desktop Environments
---

### Post by Lamaboy on 2010-08-29
When I load Ubuntu, it goes to the desktop screen, shows my desktop picture, loads Pidgin which I have set to start on startup, loads Icons, and then the screen goes black. The mouse cursor shows up, I can move it around, and then it goes black again, and the mouse cursor shows up again. This repeats a few times until the cursor freezes. 
This started happening after I tried fixing a bug with new drivers for my Intel 845gl video card. The instructions I followed are these: 
```
To use the available fix, run the following commands:
 apt-add-repository ppa:glasen/855gm-fix
apt-add-repository ppa:brian-rogers/graphics-fixes
apt-add-repository ppa:glasen/intel-driver
aptitude update
aptitude install linux 855gm-fix-dkms
aptitude dist-upgrade

```,taken from [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492").
I have tried some of the options in recovery mode from GRUB menu, none really work, except booting with default graphic configuration, or something similar like this. 

Anyone have any ideas? 

If you need more information, let me know.
Thanks,
Lamaboy

---

### Post by Lamaboy on 2010-08-29
Didn't see anything against this in code of conduct so...bump.

---

### Post by silbak04 on 2010-08-30
As far as I am concerned an 855gm and an 845gl video cards are two different one's...you 
want to get a driver for your 845gl on board video card rather than install the 855gm driver.
That may be why you're experiencing this problem...

---

### Post by Lamaboy on 2010-08-30
That could be it. I am going to do some homework and figure out how to install drivers for specific things, and I will post back if it works out. 
Thanks for a reply though, only one!

---

### Post by Lamaboy on 2010-08-30
It tells me when going into recovery mode the following:
(EE) Intel(0): I830 Dma cleanup failed
(EE) intel(0): failed to destroy server context
Any idea what that means?

---

### Post by silbak04 on 2010-09-01
This could be a mtrr issue...what's your output for ```
$ cat /proc/mtrr
```

---

