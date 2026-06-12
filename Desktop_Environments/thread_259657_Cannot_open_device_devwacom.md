---
title: "Cannot open device /dev/wacom"
date: 2006-09-17
forum: Desktop Environments
---

### Post by reskerix on 2006-09-17
I'm reciving the error:
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument

on the /var/log/Xorg.93.log file every time I try to start the X in normal mode. 

The only solution I've is to run X is start them in 'a prueba de errores' (safe mode?) but I want to solve this problem.

Any suggestions?

Thanks.

---

### Post by mitch.c on 2006-09-17
> **reskerix said:**
> I'm reciving the error:
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument

on the /var/log/Xorg.93.log file every time I try to start the X in normal mode. 

The only solution I've is to run X is start them in 'a prueba de errores' (safe mode?) but I want to solve this problem.

The default xorg.conf ships with the wacom device support (presumably for tablet pc support). If you don't have the device, you get the error. It's harmless really, but you could modify your xorg.conf.

Your call.

---

