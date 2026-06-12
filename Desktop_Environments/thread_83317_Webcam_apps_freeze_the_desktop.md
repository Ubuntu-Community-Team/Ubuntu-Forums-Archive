---
title: "Webcam apps freeze the desktop"
date: 2005-10-28
forum: Desktop Environments
---

### Post by telex4 on 2005-10-28
I've just got a Sweex 100k webcam. The drivers load up fine, but as soon as I initialise it with GnomeMeeting, camorama or gqcam my computer freezes. When I use sonic-snap and v4l-conf I get this output:

>  tom@piglet ~ $ sonic-snap-gui
Clock resolution is 999848 nanoseconds
/dev/video0 is no V4L2 device

tom@piglet~ $ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xf8000000
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Invalid argument
/dev/video0 [v4l]: no overlay support 

I've tried it on my old Gentoo system and it works fine with sonic-snap, and gqcam didn't crash my computer although it did fail to work (complaining that no image was found), so it must be someting to do with Kubuntu. I'm on Breezy... Any thoughts?

---

### Post by telex4 on 2005-10-28
If it's any help, here's the full syslog output when I first plug the camera in:

> 
Oct 28 17:16:14 localhost kernel: [  430.240140] usb 1-1: new full speed USB device using ohci_hcd and address 3
Oct 28 17:16:15 localhost kernel: [  430.620470] Linux video capture interface: v1.00
Oct 28 17:16:15 localhost kernel: [  430.676855] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera found. SONIX sn9c102 + Pas106
Oct 28 17:16:15 localhost kernel: [  430.685786] usbcore: registered new driver spca5xx
Oct 28 17:16:15 localhost kernel: [  430.685800] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57.02 registered
Oct 28 17:16:15 localhost usb.agent[5529]:      spca5xx: loaded successfully
Oct 28 17:16:15 localhost kernel: [  430.778264] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24
Oct 28 17:16:15 localhost kernel: [  430.786683] usbcore: registered new driver sn9c102
Oct 28 17:16:15 localhost usb.agent[5529]:      sn9c102: loaded successfully


---

### Post by cowlip on 2005-11-03
Hey, this may be this bug [https://bugzilla.ubuntu.com/show_bug.cgi?id=15809](https://bugzilla.ubuntu.com/show_bug.cgi?id=15809) [https://bugzilla.ubuntu.com/show_bug.cgi?id=14566](https://bugzilla.ubuntu.com/show_bug.cgi?id=14566)

---

### Post by hunteramor on 2005-12-07
same problem here - any workarounds?   ](*,)

---

### Post by telex4 on 2005-12-07
I installed this version of the spca5xx driver:

[http://mxhaard.free.fr](http://mxhaard.free.fr)

Then I manually removed both the webcam drivers that got installed automatically, re-modprobed the spca5xx driver, and only used V4L v1 apps. Not perfect, but it works well enough.

---

### Post by invalid on 2005-12-07
I used the debian packaged driver:
[http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source)

Cb

---

### Post by arnieboy on 2005-12-10
just follow this howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

