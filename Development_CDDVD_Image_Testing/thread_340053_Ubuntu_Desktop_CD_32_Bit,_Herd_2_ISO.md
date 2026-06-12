---
title: "Ubuntu Desktop CD 32 Bit, Herd 2 ISO"
date: 2007-01-16
forum: Development CD/DVD Image Testing
---

### Post by sloggerkhan on 2007-01-16
Hey there.

I have an Acer w/ x700
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985)

I just wanted to note that the live CD continues to exhibit the same bug for this set of laptops that has been around since 6.06 or maybe earlier.

Splash option on boot will cause console corruption, so you must boot without splash. Then you must go to a console when it boots and add:
under xorg.conf section device:
Option "Monitor Layout" "LVDS, CRT"

and restart x to get the live CD working.


Edit: side note: you also still have to sudo modprobe tifm-sd to get the card reader active.

---

### Post by sloggerkhan on 2007-01-17
I'd also like to note that the live cd froze at the paritioner, though this might have been a bi-product of having a dream linux install. (Not sure, but dream linux seemed to screw up all my Ubuntu partitions.)

---

