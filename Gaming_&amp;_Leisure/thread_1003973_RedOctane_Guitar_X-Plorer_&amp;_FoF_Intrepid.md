---
title: "RedOctane Guitar X-Plorer &amp; FoF Intrepid"
date: 2008-12-06
forum: Gaming &amp; Leisure
---

### Post by linuxn0b on 2008-12-06
I've been reading the forums for the past few days and trying to get my Guitar Hero controller to work on Intrepid for Frets on Fire.

The native xpad module seems to recognize the guitar correctly as a RedOctane X-Plorer, and I've even compiled and used the xboxdrv libusb layer.  The xboxdrv program recognizes the controller and detects all of its keypresses, but I cannot get FoF to map any of the buttons of the controller in the game for either of the above methods (xboxdrv or xpad).  Does anybody have any ideas on what I could do?

I've tried to use jscalibrator, but it doesn't seem to recognize any kepresses.  I really want to play FoF, but don't want to have to boot into Windows to do so:(

Any help would be much appreciated.

Thanks,
Jonathan

---

### Post by Grumbel on 2009-01-02
Make sure that you have access to the joystick device and that it reports events:

jstest /dev/input/js0

If that works, games should recognize the buttons, if it doesn't work, you have to find out whats wrong. Likely problems are lack of permissions and Xorgs new hotplug, see:

[http://pingus.seul.org/~grumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README](http://pingus.seul.org/~grumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README)

for workarounds.

---

### Post by linuxn0b on 2009-01-07
Thanks for your reply!  The workarounds worked perfectly for me and I'm now fretting away

---

### Post by fragmental on 2009-02-05
I've tried to use the native xpad driver and it looks like it works fine in dmesg, but doesn't recognize any keypresses in frets on fire or jstest or jscalibrator.

Are you using xboxdrv or xpad?  Which workarounds did you use?

---

### Post by Grumbel on 2009-02-05
> **fragmental said:**
> I've tried to use the native xpad driver and it looks like it works fine in dmesg, but doesn't recognize any keypresses in frets on fire or jstest or jscalibrator.
Make sure that your joystick isn't grabbed by Xorg, see the Xorg Trouble section in:

[http://github.com/Grumbel/xboxdrv/blob/fdadf215b76dfd6b9d5f5fb4b7645b48687ca668/README](http://github.com/Grumbel/xboxdrv/blob/fdadf215b76dfd6b9d5f5fb4b7645b48687ca668/README)

for fixes. To find out of if the joystick is grabbed type "xinput list", when they joystick/xpad is listed there its grabbed.

---

### Post by janicejan on 2009-02-05
I just hope frets on fire can be played online, that way we can challenge each other ;), I'm really good at it...

---

