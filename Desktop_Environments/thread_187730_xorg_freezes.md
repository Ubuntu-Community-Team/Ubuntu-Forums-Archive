---
title: "xorg freezes"
date: 2006-06-03
forum: Desktop Environments
---

### Post by maljcik on 2006-06-03
Hi,

this is my first time to use ubuntu... I d/loaded the install cd.. when it first booted up it crashed before launching gnome, thou after a restart gnome started ok. So I continued with installation but found out that the behaviour (unexpected crashes of the x server probably) remains. At first I thought that it might be a gnome-only problem, so I tried installing and using kde. What happens:

- system boots up correctly.
- most of the time, the GUI login app (dunno the name sorry, used to start desktop by startx from shell) where one can chose what DM to use launches, but sometimes I just end up with a dark screen, keybord not reacting, no mouse cursor..
- if i successfully get to the GUI login app, i can use gnome or kde without problems.
- logging off sometimes succeeds and I end up in the "GUI login app" sometimes I get a blank screen.

I had a look into /var/log/xorg.0.log to find this...:

```
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
my xorg.conf set by the installer

```
Section "Device"
	Identifier	"ATI Technologies, Inc. R200 BB [Radeon All in Wonder 8500DV]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

.. any suggestions? tia, Honza

---

### Post by JoWilly on 2006-06-03
The /dev/wacom errors are not a problem.

Try to disable agp and reboot to see if this fixes it (agp is often the reason).

---

