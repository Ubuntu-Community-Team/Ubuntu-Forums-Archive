---
title: "Device troubles"
date: 2010-09-08
forum: Desktop Environments
---

### Post by marcusdufrane on 2010-09-08
Runnning Ubuntu 8.04 off of a 4GB usb drive.

I am having an intermittent problem with the os loading the touchscreen device.
Most of the time everything loads and works perfectly, but once and a while the touchscreen device doesn't work.

Looking at the log files i think i may have narrowed down part of the problem with in the Xorg log.
it seems that when the device works the driver is loaded and the device is set fine and this message is seen...

elo touchscreen on. local->fd ffffffff..
 After open. local->fd 11(or whatever number is assigned)

and when the device fails this message is present.

elo touchscreen on. local->fd ffffffff..
 After open. local->fd ffffffff
Unable to open elo touchscreen device: No such file or directorycouldn't enable device 4

So, can anyone shed some light on what may be going on here?

---

