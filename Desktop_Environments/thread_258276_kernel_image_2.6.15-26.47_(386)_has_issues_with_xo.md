---
title: "kernel image 
2.6.15-26.47 (386) has issues with xorg ati driver"
date: 2006-09-15
forum: Desktop Environments
---

### Post by sbrydon on 2006-09-15
On updating my kubuntu system to the latest kernel image and restricted modules (2.6.15.11-4) my X session fails to start and my system is locked up on a blank screen.

My xorg.conf driver is the xorg ati driver. Once I changed the driver to vesa my machine booted correctly.

As an aside - when I build a custom kernel using the 2.6.15-26.47 kernel my machine boots OK using the xorg ati driver except my keyboard and mouse don't work so therefore I can't log in and can't change to a console. 

Just my experience - may be useful to others.

---

### Post by sbrydon on 2006-09-15
I was wrong about the problem with the standard 386 kernel and xorg ati drivers. It may have been that my system was not reset enough in between boot...

The keyboard lock I experience with my own custom kernel (built from the ubuntu source package) goes away if I deselect the kernel config option for SMP. Weird...

---

