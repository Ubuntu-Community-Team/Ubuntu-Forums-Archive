---
title: "X won't start after 10.10 upgrade"
date: 2010-10-01
forum: Desktop Environments
---

### Post by vibrunazo on 2010-10-01
Upgraded from 10.04 to 10.10, gnome didn't load on reboot, tried typing **startx** and got this error:

```
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found
```

I had the nvidia proprietary driver installed before upgrade. Using a nvidia g-force 7300 graphic card.

Anything I can do on my end to fix this? Any easy way to go back to 10.04? Or should I just reinstall 10.04 from the CD-ROM and forget about 10.10 before it's stable?

---

### Post by sikander3786 on 2010-10-01
Isn't it the old famous bug?

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394)

[http://ubuntuforums.org/showthread.php?t=1566254](http://ubuntuforums.org/showthread.php?t=1566254)

---

### Post by ajgreeny on 2010-10-01
You just need to install the video driver for the new kernel, I expect, which you can either do from the cli, if you know the driver package name (I don't, I have an ati card) or you can choose failsafe gnome from the session menu at login, and do it in the low resolution screen that should appear.

---

### Post by satwien on 2010-10-03
Try driver 256.53 on kernel 2.6.35.22. This was the only solution for me, on a 64bit Ubuntu.

---

