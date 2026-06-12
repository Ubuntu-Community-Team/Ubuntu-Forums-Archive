---
title: "Problems with xpad"
date: 2008-09-01
forum: Gaming &amp; Leisure
---

### Post by Lyon on 2008-09-01
xpad seems to be extremely finicky for me. I've gotten it to work on a few occasions, but on every occasion I've had to restart my computer after unplugging the controller (and then plugging it in again later) to get the module to run again. (Note the controller needs to be unplugged when booting or else my system will freeze on boot). On a couple occasions, overwriting xpad.ko in the */lib64/modules/2.6.24-19-generic/kernel/drivers/input/joystick* directory with the original xpad.ko using nautilus has worked.

What seems to be confusing me the most is that the module SEEMS to be working, as there are js0, js1, and js2 in the */dev/input/* directory, but when I run jscalibrator, it gives me the following error in the gui:

> Joystick Initialization Failed

Could not access the specified path(s), verify that the path(s) are specified correctly and that you have sufficient permission to access them. Also, make sure that the joystick in question is actually connected, turned on (as needed), not in use by another program, and the joystick driver or module is loaded (type 'modprobe <driver name>').


This is leading me to believe that the problems lies either with the driver, something I'm doing, or the fact that the module just simply doesn't have permission to access the */dev/input/* directory.

I've tried running:
```
sudo modprobe xpad
```
but everytime I do, the terminal seems to get "stuck" in the command (new command line does not appear after I send that command)

If anyone needs any more details, just ask, I figured this might be enough, but I'm pretty new to linux in general, so I don't know.

---

