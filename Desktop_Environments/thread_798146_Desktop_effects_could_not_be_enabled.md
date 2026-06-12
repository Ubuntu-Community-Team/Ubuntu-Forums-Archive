---
title: "Desktop effects could not be enabled"
date: 2008-05-17
forum: Desktop Environments
---

### Post by - 000 - on 2008-05-17
I use to be able to have "Extra" visual effects on Ubuntu, but now it says "Desktop effects could not be enabled".

My GPU is:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by EXCiD3 on 2008-05-17
Do you have the intel graphics drivers installed?

---

### Post by - 000 - on 2008-05-17
Where can I find them?

---

### Post by EXCiD3 on 2008-05-17
Sorry, it looks like this driver should come enabled by default. Does System > Administration > Hardware drivers list your card?

---

### Post by - 000 - on 2008-05-17
No, it is not.

I installed my OS on a seperate partition.  Do you think I should just reinstall?

---

### Post by EXCiD3 on 2008-05-17
It should work out of the box but it isnt for some reason. On the LiveCD were you able to enable the desktop effects? You may want to reinstall since i cant seem to find anyone else with this problem. :(

---

### Post by ubuchignome on 2010-04-17
In the Synaptic package manager make sure this is installed and try the recommended video driver Nvidia. It should be installed by default, but check. 

X.Org X server -- Intel i8xx, i9xx display driver

This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

This package also provides XvMC (XVideo Motion Compensation) drivers
for i810/i815 and i9xx and newer chipsets.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xf86-video-intel driver module.

Canonical provides critical updates for xserver-xorg-video-intel until April 2011.

---

### Post by appier on 2010-05-06
I have the same problem here, and found a lot of information on this problem/bug at:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

---

