---
title: "What else needed to support dual monitors?"
date: 2014-01-18
forum: Desktop Environments
---

### Post by ruwan2 on 2014-01-18
Hi,
I accidentally find a post mention dual monitors and xubuntu Desktop Systems. After I install xubuntu Desktop Systems, I do not find a configuration to turn on dual monitor. My computer is an AMD CPU, ATI graphics card which has one DVI one VGA. In Windows 7, it works well with dual monitors. Now in Ubuntu 12.04, 32-bit, it has duplicate pictures on two monitors. I am new to xubuntu. Do I need Xfce or something else?


Thanks,

---

### Post by TheFu on 2014-01-18
[http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver) this works for nVidia. I suspect the ATI version will work similarly, but I've never connected an ATI-GPU to multiple monitors. Sorry.

---

### Post by jp734 on 2014-01-19
Preferably, just add a device and monitor configuration files on /usr/share/X11/xorg.conf.d folder.

---

### Post by coffeecat on 2014-01-19
@ruwan2, I was able to set up dual monitors in Xubuntu 12.04 using an ATI/AMD card with a little fiddling. This was using the default open source driver with a Radeon HD6450 graphics card. What is your video card?

The how is in this thread:

[http://ubuntuforums.org/showthread.php?t=1982974](http://ubuntuforums.org/showthread.php?t=1982974)

Make sure you read the askubuntu link in my post #6 in that thread. The method involves getting some information from the xrandr terminal command. If you prefer a GUI for that bit, I believe the package arandr will provide that, but the instructions in the askubuntu link are quite clear. Post your output of xrandr if you get stuck.

**EDIT**:

> **ruwan2 said:**
> Do I need Xfce or something else?

Just to add - you already have Xfce. Xfce is the name of the desktop environment in Xubuntu. The problem you have encountered is that even if your video card/driver combination can support dual monitors, the Xfce desktop - or at least the version in 12.04 - does not have suitable GUI configuration utilities built in. You either have to install the proprietary driver and rely on the GUI configuration utility that comes with that, or if you want to use the default open source driver, use xrandr as in the askubuntu link.

---

