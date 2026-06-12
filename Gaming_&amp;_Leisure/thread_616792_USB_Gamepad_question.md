---
title: "USB Gamepad question"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by tamcdonald on 2007-11-18
Hi. I've been trying to get this old Nyko Air Flo usb gamepad working. I'm installed jscalibrator and loaded it, but when it loads it open /dev/js0 and reports at the top of the screen that it's a Microsoft Sidewinder Mouse, which is the actual mouse I have installed. Why is my mouse on js0 and and how can I configure this gamepad? I try selecting /dev/js1 but it always says SIdewinder Mouse. Any help is appreaciated.

---

### Post by acoustibop on 2007-11-19
Your controller should actually be at /dev/input/js0, tamcdonald.  Either point jscalibrator at that location (and other applications) or put a symlink to js0 in /dev so applications can find it there.  The latter is probably the better solution, as not all applications can easily be configured to look for a controller other than /dev/js0.

However, I'd recommend getting rid of jscalibrator unless you're using it in Kubuntu (where it's included in the OS installation, and seems to work OK).  It has an annoying habit of disabling the direction buttons/sticks of controllers - they appear as working in jscalibrator, but won't work anywhere else.

---

### Post by tamcdonald on 2007-11-19
Ok, I got the pad sort of working. But now I seem to have the problem of no d-pad or analog sticks. I've uninstalled jscalibrator, but no luck. Anyway to fix this?

---

### Post by acoustibop on 2007-11-20
Make sure you remove the jscalibrator configuration, tamcdonald.

---

