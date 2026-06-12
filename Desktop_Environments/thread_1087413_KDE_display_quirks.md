---
title: "KDE display quirks"
date: 2009-03-05
forum: Desktop Environments
---

### Post by snorkytheweasel on 2009-03-05
Intrepid server 64-bit with KDE. 
22" widescreen monitor capable of 1600 x 1024

[LIST=1]
[*]Everything on the screen is "fat." It looks like 640 x 480 (or worse).  I suspect that I might need a linux video driver. How do I find out which video system I have and what driver I am using? How do I adjust the screen resolution?
[*]I've lost the horizontal panel from the bottom of the display. How do I get it back?
[*]The KDE button has migrated from the lower-left-hand corner to the "top" of the screen. Unfortunately, it is covered by what appears to be a black panel: full-width horizontal, 3/4" high, completely blocking use of that area od the display. What is this? How do I get rid of it?
[/LIST]

---

### Post by crypto2600 on 2009-03-05
What video card do you have?

---

### Post by snorkytheweasel on 2009-03-05
The graphics are integrated in the mobo. Chipset: nvidia geforce 6150 LE (NFORCE 430). NVIDIA has a Linux driver specific to this chipset and 64-bit AMD. I thought that this driver was built in to Ubuntu, but I can't figure out how to tell Ubuntu to use this driver.

---

### Post by yther on 2009-03-05
Yes, that sounds like a good place to start.  :)

One word of advice, from personal experience:  Do not load the 180.35 drivers (nvidia-glx-180) if you have KDE 4.2.  I had various display glitches using those, which were solved when I reverted to 180.29.  Also, be aware that you should load all of the packages with the same prefix, except the -dev ones.  For example:

```
i A nvidia-180-kernel-source        - NVIDIA binary kernel module source
i A nvidia-180-libvdpau             - Video Decode and Presentation API for Unix
p   nvidia-180-libvdpau-dev         - Video Decode and Presentation API for Unix
i   nvidia-180-modaliases           - Modaliases for the NVIDIA binary X.Org dri
i   nvidia-glx-180                  - NVIDIA binary Xorg driver
p   nvidia-glx-180-dev              - NVIDIA binary Xorg driver development file
```

(Don't worry about the "libvdpau" stuff on mine; that's a special one I loaded for better performance with certain types of video files.)  Notice the "i" before 4 of those, which means those 4 are **i**nstalled.  You need all related packages, otherwise you can wind up getting no usable displays when you start up.

I almost forgot:  To force a specific version, use Synaptic and the "Force Version" item under the Package menu.  You will then get a list of available versions.

Good luck!  :KS

---

