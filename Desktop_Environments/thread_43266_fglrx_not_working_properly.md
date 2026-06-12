---
title: "fglrx not working properly"
date: 2005-06-21
forum: Desktop Environments
---

### Post by bobgreen5s on 2005-06-21
My ATI Radeon 9600XT was getting 1000-1200fps in glxgears so I decided to install the FGLRX 8.14.13 drivers following the howto guide here: [http://www.ubuntuforums.org/showthread.php?t=32495&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=fglrx) . I did everything correctly and installed linux-headers and restricted modules for my kernel version and yet I can't get 3D acceleration enabled. 
This is the error output of /var/log/Xorg.0.log
```
**cat /var/log/Xorg.0.log**
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

Any help is appreciated.

---

### Post by bobgreen5s on 2005-06-21
argh...

---

### Post by Zeroedout on 2005-06-21
haha, yea, it's a bitch. I bet you didn't move fglrx.ko from /lib/modules/fglrx/ TO /lib/modules/2.6.10-5-686/kernel/drivers/video/ did you? ofcourse, just replace 2.6.10-5-686 to whatever kernel you have installed. Ofcourse, use either use sudo mv or sudo nautilus to accomplish this

---

