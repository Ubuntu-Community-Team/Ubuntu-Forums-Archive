---
title: "Toshiba Tablet and Jaunty"
date: 2009-05-02
forum: General Help
---

### Post by kingfinny on 2009-05-02
All,

I'm pretty much a n00b to linux, at least as far as fiddling with configurations and hardware setups.  I recently picked up an old Toshiba Tecra M4 tablet notebook on the cheap, sans OS, and threw Jaunty on to see how far it would get me.  Turns out, it gets me pretty far.  Out of the box the touch screen and stylus work, although the eraser end does not.  The only thing that I can't do is rotate/invert the screen when I twist the lid into 'tablet mode'.  I've looked at a number of threads and tried a bunch of stuff, but everytime I end up in a worse situation than where I began.  I've tried xorg.conf hacking, but evidently Juanty is deprecating that sort of thing and moving to HAL.  I've tried creating and editing .fdi files, but also to no avail.  I've seen a few scripts for screen rotating, but I haven't been able to follow the instructions closely enough to make those work either.  

Ideally I'd like to be able to press the button on the lid that is marked for screen rotation and have the screen flip.  I know it triggers an event (using acpi_listen), so I imagine I need a script that listens for that and triggers the rotation.  Anyone got anything?

---

### Post by Favux on 2009-05-02
Hi kingfinny,

If when you type "xev" in a terminal and press the rotate button it returns a keycode, like say keycode=154, then you should be able to bind the key to a rotation script.  Discussed here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

But what you need to know is that with the current linuxwacom 0.8.2-2 "native" to Jaunty (specially patched to support Xserver 1.6 and HAL) there is a "bug".  The callout in the 10-wacom.fdi file is returning HAL/D-BUS names that linuxwacom doesn't recognize.  Hence xsetwacom commands don't work (no rotation of Wacom input devices) and so "wacomcpl" (tablet calibration gui) doesn't work.  Work arounds discussed in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  On the same page, section 3, discussed calibration.

I think the Tecra M4 is a serial Wacom tablet pc, isn't it?  If so all you need is rec's script and you can ignore the rest.

---

### Post by kingfinny on 2009-05-02
Yes, I can get a keycode for the screen button using xev.  Hopefully that will come in handy in the future.  

Unfortunately, none of the other HOWTO's seem to work for me.  When I try to install linuxwacom 0.8.2-2 I get a missing .h error (xf86Version.h I think).  I then tried linuxwacom 0.8.3-3, and it works until I restart.  Then I get loads of startup errors from the xorg.conf.  I feel like I'm moving backwards.  If the touchscreen and stylus are working right after a fresh install, why should I need to reconfigure and recalibrate them via xorg or wacom utils?

---

### Post by Favux on 2009-05-02
Hi kingfinny,

I'm sorry, I wasn't telling you to recompile linuxwacom.  Since you have a serial tablet the only thing you need to do is deal with the "names" HAL is returning.  Jaunty Users describes two ways to do that.  One is to use rec's script (called wacomtohal) to translate the HAL names to ones linuxwacom understands.  The other one in 3) is to use the HAL names and substitute them for linuxwacom names in things like a rotation script.  So in 1) all you need is the script.  All the rest you can ignore, that's for usb tablets.  You can use the default patched 0.8.2-2 linuxwacom that comes with Jaunty.  Then you calibrate with wacomcpl (Section 3).

---

