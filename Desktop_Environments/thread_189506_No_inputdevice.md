---
title: "No inputdevice"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Epimetheus on 2006-06-05
When i boot with the liveCD all works excellent, except the network sometimes, but when i've installed everything and reboots in the local copy i get no response what so ever from my keyboard and mouse, my wireless mouse has a tiny light that says when it gets a signal from the computer and that light does not say anything during the boot up as it usually does.

Oh and after a few seconds of not being able to do anything it locks up and the text indicator stops flashing. ](*,) 

Anyone got an idea?

---

### Post by Epimetheus on 2006-06-06
bump

---

### Post by Epimetheus on 2006-06-14
Ok checked the xorg.conf files and there where basically no difference between the livecd and the installed version.

bump

[EDIT]
I i've checked the error logs too... dug out these errors:
/var/log/syslog:
> Jun  5 16:15:14 toby-desktop kernel: [   38.966441] psmouse: probe of serio0 failed with error -1
/var/log/Xorg.0.log:
> (EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success

is there anything i've missed?
[/EDIT]

---

