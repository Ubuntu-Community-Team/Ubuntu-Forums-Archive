---
title: "How would I set processor speed at boot?"
date: 2009-06-12
forum: General Help
---

### Post by mjpatey on 2009-06-12
Hi, all-

I have the CPU Frequency Scaling Monitor installed on my Gnome panel, and it works fine.  But when I first boot, Ubuntu defaults to the "Ondemand" profile, which dynamically changes the CPU speed based on need.  This computer is a desktop system, and I want it to always boot into "Performance" mode (100% speed at all times).

How do I make it default to 100% CPU on boot?

Thanks!

-Mark

---

### Post by 3rdalbum on 2009-06-12
"Ondemand" is still the recommended mode for desktop systems. When there is noticable load, the CPU turns up to your full speed so you have full power. When there isn't much load, the CPU turns back to the lower speed to save electricity and heat. But I'll tell you how to make it go full-steam-ahead anyway:

You can either turn off speed stepping in your BIOS, or put the following into your /etc/rc.local file:

```
echo "performance" >> /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

That turns the governor to "performance" on the 1st CPU core. If you're on a dual-core, copy and paste the line again and change "cpu0" to "cpu1" to set the 2nd core to "performance". If you're on quad-core, you need four such lines referencing "cpu0", "cpu1", "cpu2", and "cpu3". Computers count from zero, you see.

Reboot, and you will have full power when the X server starts. If you turn off speed stepping in the BIOS you will have full power before GRUB loads.

---

### Post by mjpatey on 2009-06-12
Thank you!  I couldn't find this info anywhere in the forums, via Google or any other means.  I will give this a shot.

For some reason, in Ondemand mode, the switching lags behind the need for speed.  When I first open a program, it takes longer to load in that mode, and the tray applet still shows 37% for quite a while.  Just doesn't feel snappy.  Of course, it could just be psychological...

I'll post back with results.  Thank you again!!!

-Mark

---

