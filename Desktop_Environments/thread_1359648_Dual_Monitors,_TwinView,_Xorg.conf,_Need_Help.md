---
title: "Dual Monitors, TwinView, Xorg.conf, Need Help"
date: 2009-12-19
forum: Desktop Environments
---

### Post by ZER01NE1NE on 2009-12-19
Hey everyone,

I have a dual monitor setup on my freshly installed Ubuntu 9.10, and I'm trying to configure it. So I run:

```
gksudo nvidia-settings
```but when I try to save the xorg.conf file, it tells me that there was an error parsing the file or something like that. So I opened up xorg.conf and this is what I saw:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```In previous versions of Ubuntu, it always generated a much more detailed xorg.conf. Why so minimal in 9.10?

I also tried

```
sudo dpkg-reconfigure xserver-xorg
```but that didn't seem to do anything.

So I decided that the best thing to do is to create xorg.conf myself, but I'm having a hard time finding a comprehensive tutorial on how to do so. Here's xorg.conf as it is right now:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "RenderAccel"    "true"
    Option    "Twinview"
    Option    "MetaModes"    "1680x1050 1680x1050"
    Option    "TwinViewOrientation"    "Above"
EndSection

Section "Module"
    Load    "nv"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```I want to switch which monitor is the primary monitor, and I want to keep TwinView. Oh, and I also don't want to switch which monitor goes to which port on the video card. If anyone can help me out, that would be very much appreciated. Thanks in advance.

~ Kyle

---

### Post by Robstarusa on 2009-12-20
Try this:

from a terminal:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-`date +%s`
then gksudo nvidia-settings.

After getting everything set there, save to xorg.conf.

Then stop & restart gdm.  You should be set!

Rob

---

### Post by ZER01NE1NE on 2009-12-20
Yay, it worked! :) Thanks Rob! I was expecting this to be a long, drawn-out and painful process involving lots of crashes and whatnot, but that was really simple. Thanks again.

~ Kyle

---

