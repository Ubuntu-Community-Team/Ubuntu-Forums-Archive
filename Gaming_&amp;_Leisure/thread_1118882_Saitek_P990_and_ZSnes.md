---
title: "Saitek P990 and ZSnes"
date: 2009-04-07
forum: Gaming &amp; Leisure
---

### Post by Inquisitorthemad on 2009-04-07
I purchased a Saitek P990 dual analog pad from CCL Computers, with intent to use it with ZSnes.

If I calibrate it with jscalibrator (which DOES recognise the D-pad and the analog sticks) then the program notices button presses, but not the D-pad, or either analog stick.

If I don't calibrate it with jscalibrator, the program doesn't even recognise the buttons.

Either way, the D-pad doesn't work, and neither do the analog sticks.

I tried Joy2Key, but I could hardly understand it, much less use it properly.

Help please?

---

### Post by dfreer on 2009-04-08
The problem is likely due to jscalibrator itself: For a long time users have reported issues with jscalibrator but it has yet to be fixed. I don't know why people install it in the first place.

The symptoms always seem to involve: (1) All buttons appear to work in the jscalibrator program (2) Any other program the axis/dpad does not work at all.

You'll want to google on the exact method of removing jscalibrator (there as been plenty of posts about it in these very forums) as it is not enough to simply uninstall the program; IIRC it involves removing a hidden file in your home folder.

Once you have it removed, reboot. Don't install any calibrator as IMO it's often not needed, just try ZSNES again and see if any/all keys register. If it still doesn't work, try pSX or another program that can use the gamepad and see if it works with that.

> If I don't calibrate it with jscalibrator, the program doesn't even recognise the buttons.

I'm pretty sure I've heard of users successfully using the P990 as it uses a standard USB HID driver. Did you try using the controller first in ZSNES before you installed jscalibrator and it didn't work? There is a common issue with USB devices, in windows and linux, that programs often won't be able to see/recognize the device if you insert it while the program is running; you have to start the program after you have inserted your USB device. Perhaps this was your issue?

---

### Post by hikaricore on 2009-04-08
Working fine for me without the need for jscalibrator, as dfreer suggested I also belive your problem lies there.

---

### Post by OrangeVixen on 2009-10-25
Do not use jscalibrator for game pads, it's for sticks.

---

