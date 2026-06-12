---
title: "Thinkpad x1 carbon (2014) random, phantom keystrokes - GNOME"
date: 2018-01-06
forum: Desktop Environments
---

### Post by bvz on 2018-01-06
I just installed 16.04 LTS GNOME onto a 2014 Thinkpad X1 carbon (i5, 8GB RAM).

I completely wiped out Windows, repartitioned the 180GB drive into a single 8GB partition for swap, 20GB partition for /, and the remainder in a partition for /home

The only software I have installed is Chrome and QEMU.  I haven't actually used QEMU yet (I started to install windows 10, but it died on me part way through so I bailed and restarted).

If I start the computer up and just let it sit without touching anything I am getting phantom keystrokes showing up.  The volume will spontaneously change (nothing is playing, but I can see the volume icon show up). Files windows will suddenly appear.  Menus will appear and then disappear.  The main meta key will be hit (I can see all of the other windows shrink down).

It seems to happen at a fairly leisurely pace.  Over the course of 15 minutes I will get somewhere around 10-20 keystrokes that I can observe.

I opened a gedit window to see if I could capture any of the keystrokes, but it appears the all the keystrokes are all meta-keys, and not just regular keys that one would type into a text window.

I am pretty technical and have experience with Linux on a reasonably high level, but am by far from a sys admin level user.

Does anyone have any thoughts on what might be happening or how I might start diagnosing it?  So far a google search for this problem only shows up posts from more than 4 or 5 years ago, and most of those were resolved as a consequence of wireless keyboards.

Edit #1:
This model has what they call an "adaptive" keyboard.  The function keys are not physical keys, but rather a row of touch sensitive buttons whose icons change to indicate different functionality.  I can watch as the icons shift around from one set (the function keys) to another (volume, brightness, etc) without me doing anything.  I wouldn't be surprised if this stupid thing is part of the problem (as it isn't just a simple keyboard because of this foolishness).  Don't know how to solve it, but I suspect this is a clue.

Edit #2:
Confirmed that it is the adaptive keyboard.  Every thing that it is doing on its own I can reproduce by hitting one of those "keys" when it is in different modes.  That includes turning the keyboard backlighting on and off, enabling and disabling the wireless, opening the control panel window, opening the files application windows, etc.  The only issue is that it does all of that by itself (I can see the keyboard backlight turning on and off etc.)  I'm trying to find out if there are specific drivers for this keyboard that I can download somewhere.

---

