---
title: "FGLRX Problems"
date: 2007-05-24
forum: Desktop Environments
---

### Post by Caligula on 2007-05-24
RIght, it's about time I've asked here what to do, I'm completely puzzled.

I've tried installing fglrx for my Radeon Xpress 1100 IGP card. I've followed the instructions [here ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2")to install the driver from ati.amd.com, I've blacklisted fglrx in /etc/default/linux-restricted-modules-common.

After everything, I still get this output:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Needless to say, 3D acceleration doesn't work.

I've tried the Mesa fix:
```
sudo mkdir -p /usr/X11R6/lib/modules/dri  
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

It didn't help.

I've checked my /var/log/Xorg.0.log file and noted the following sections:

> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"


> (II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


If anyone can please tell me what to do I'll be greatful for eternity [-o<:sad:
I'm using ubuntu Feisty on a new Dell Inspiron 1501.

---

### Post by scottDkoDer on 2007-05-24
while I have a different setup than yours (Dell Desktop w/ATI 9600), I had some trouble installing fglrx.  I found that I couldn't have all of my monitors plugged in on boot.  So, if you have a dual monitor setup, unplug everything from your card except your main monitor.  Then, if you are running ubuntu, google 'fglrx debian' or the like, and find a tutorial.  Exit from gnome/X (reboot into failsfe/root) and install driver.  Search for xorg.conf file configurations to set your card up the way you want.  Hope this helps.
;)

---

### Post by Caligula on 2007-05-24
unfortunately not, but thanks anyway :/

I mean, everything is installed and all, just for some reason the modules won't load... :/

---

### Post by Caligula on 2007-05-24
Solved it!

Running the command depmod -ae has solved it. Thanks to Coldwar55 from this thread: [http://kubuntuforums.net/forums/index.php?topic=3082899.msg69173#msg69173](http://kubuntuforums.net/forums/index.php?topic=3082899.msg69173#msg69173)

:)

---

### Post by scottDkoDer on 2007-05-24
Like I said... keep trying.  Search beryl yet??

---

### Post by Caligula on 2007-05-24
Beryl is up and running, and running great :D

---

### Post by sadako1 on 2007-05-28
> (II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x4000 at 0x2b7d7b814000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

So after following the tutorial I got this in my xorg.0.log (I substituted 8.36.5 for the included version)

I manually changed my xorg.conf to fglrx drivers but the fglrxinfo command provides this:

>  display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I tried to reinstall the kernel, but it aborted, saying that it was there aready, so it's obviously still got my old kernel installed and it's trying to use it with the new driver and it's not happy. How can I remove it?

Cheers in advance,
Andrew

---

### Post by forscheezee on 2007-06-01
> **Caligula said:**
> Solved it!

Running the command depmod -ae has solved it. Thanks to Coldwar55 from this thread: [http://kubuntuforums.net/forums/index.php?topic=3082899.msg69173#msg69173](http://kubuntuforums.net/forums/index.php?topic=3082899.msg69173#msg69173)

:)

Thanks for the follow up!!  Worked like a charm for me with my 9600XT 256.

Thanks again!

---

