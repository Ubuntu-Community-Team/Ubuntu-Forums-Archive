---
title: "Dual-head ATI/Radeon works with standalone CD, fails when installed on disk"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by artichoke47 on 2007-11-01
I have a new Dell computer with 
+ AMD Athlon(tm) 64 X2 Dual Core Processor 4200+,
+  ATI Radeon X1300,  
+ 2 Dell 1908FP monitors connected via digital cables
I boot CD for Ubuntu 7.10 (Gutsy) desktop AMD64. When it comes up, both monitors display the same desktop in 1280x1024 resolution. I configure for dual monitors, following instructions posted at this forum and elsewhere:
$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-generic restricted-manager
$ sudo apt-get install xorg-driver-fglrx
$ sudo depmod -a
$ sudo aticonfig --initial=dual-head --force

I have to use --force, because otherwise, aticonfig crashes without generating anything.

I restart X with ctrl-alt-bs. It comes up with 2 separate, independent  desktops on the two monitors -- exactly what I wanted! Great!

I install gutsy on my hard drive, and complete all the above steps. Now, when I restart X, it comes up in low-res failsafe mode. /var/log/Xorg.0.log tells me:
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
...but it doesn't tell me why. 

Both systems have the same versions of the kernel and the fglrx modules.
# cat /proc/version
Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007

xorg-driver-fglrx is version 7.10-8.37.6+2.6.22.4-14.9
xserver-xorg-video-ati is 1:6.7.195-lubuntu2

I have tried copying the (working) dual-head xorg.conf from the standalone system to the disk-based system, but it still boots failsafe. Even when I copy the originall single-head version from the standalone to the disk-based, I get failsafe. 

Can anyone help me unravel this?  Thanks.

---

