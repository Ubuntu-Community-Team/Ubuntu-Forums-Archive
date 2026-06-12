---
title: "XBOX USB Controller Drivers"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by AngryKidJoe on 2006-06-23
I've been searching around for this and the only thing that I've found is that the Linux XBOX ports come with them. Anyone know if there are stand-alone drivers for the USB XBOX Controller for Linux?

---

### Post by BlueFox89 on 2006-10-15
Yeah I need help too.

---

### Post by po0f on 2006-10-15
Do you need vanilla Xbox controller drivers or 360 ones?  If you are using a regular Xbox controller, you should be able to:
```
$ sudo modprobe joydev
$ sudo modprobe xpad
```
if the kernel modules aren't loaded when you plug it in.  Check to see if it worked by:
```
$ cat /dev/input/js0
```
and moving the joystick around.  If a bunch of gibberish pops up on the screen, you're good to go, just Ctrl-C and calibrate it.

If you need 360 drivers, I followed this short guide: [click](http://www.ubuntuforums.org/showthread.php?t=164040&highlight=xbox+360+kernel+module).

---

