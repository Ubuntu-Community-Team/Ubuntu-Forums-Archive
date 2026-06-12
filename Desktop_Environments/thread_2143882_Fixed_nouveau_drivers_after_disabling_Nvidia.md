---
title: "Fixed nouveau drivers after disabling Nvidia"
date: 2013-05-10
forum: Desktop Environments
---

### Post by kevpatts on 2013-05-10
Hey all,

I was having intermittent freezes with the latest nvidia drivers on my 9800 GT for ages, al through 12.04, 12.10 and still now in 13.04. Each time it would freeze I would see in /var/log/syslog:
```
NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
```
Anyway, I believe this is a bug in the nvidia drivers for old cards, so I decided to go back to the Nouveau drivers. When I switched to this driver in Software Sources => Additional Drivers and rebooted I got a low res 1024x768 desktop on a single monitor, without any graphocs accelleration. I looked into it and found in /var/log/Xorg.0.log that the nouveau driver was failing to load. It seems that this was because of a line that said:
```
[drm] KMS not enabled
```
and it kept falling back to the VESA driver instead, causing the poor graphics. I didn't have nomodeset enabled and i915.modeset=1 made no difference and I couldn't find how to enable Kernel Mode Switching (KMS) for ages and I was banging my head against the wall. I thought that kms kernel module mightbe failing to load cause it was blacklisted, but a search for kms in /etc/modprobe.d/ turned up nothing ... but then a file caught my eye! /etc/modprobe.d/nvidia-experimental-310_hybrid.conf still existed even though I had removed all nvidia drivers, and it contained the line:
```
blacklist "nouveau"
```
Ha! Thanks Nvidia you bastards! deleted the file and everything worked fine. Also added:
```
xrandr --output DVI-I-2 --right-of DVI-I-1
```
to my ~/.xprofile to configure my dual displays after login and no more need for Nvidia drivers!

Hope this helps someone.

---

