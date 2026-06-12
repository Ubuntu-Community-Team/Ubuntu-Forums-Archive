---
title: "Scrolling broken on ALPS GlidePoint trackpad in Lucid Final Release"
date: 2010-04-30
forum: Desktop Environments
---

### Post by JoeMac42 on 2010-04-30
In response to bug #550625, Chase Douglas was able to get scrolling to more or less work in Lucid  with the pre-release versions of the 2.6.32-22.33 kernels - see discussion thread here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625")
Somehow this broke when I installed the Lucid 10.04 LTS final release on my HP Mini 311 last night.

---

### Post by JoeMac42 on 2010-04-30
I downgraded linux-image-2.6.32.22-generic to version 2.6.32-22.33~pre201004281000 and edge scrolling returned to the ALPS GlidePoint trackpad.  Anyone know what happened?

---

### Post by godsbane on 2010-04-30
Just confirming this bug on the Mini 311. Little annoying, however the onlything thus far that doesn't work on this machine.

---

### Post by knifesk on 2010-04-30
just fresh installed and can't get the scroll to work... 

```
sudo xinput list-props "AlpsPS/2 ALPS GlidePoint"
```

```
Device 'AlpsPS/2 ALPS GlidePoint':
	Device Enabled (143):	1
	Device Accel Profile (261):	0
	Device Accel Constant Deceleration (262):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Synaptics Edges (279):	153, 870, 115, 652
	Synaptics Finger (280):	12, 14, 127
	Synaptics Tap Time (281):	180
	Synaptics Tap Move (282):	56
	Synaptics Tap Durations (283):	180, 180, 100
	Synaptics Tap FastTap (284):	0
	Synaptics Middle Button Timeout (285):	75
	Synaptics Two-Finger Pressure (286):	139
	Synaptics Two-Finger Width (287):	7
	Synaptics Scrolling Distance (288):	25, 25
	Synaptics Edge Scrolling (289):	1, 0, 0
	Synaptics Two-Finger Scrolling (290):	0, 0
	Synaptics Move Speed (291):	0.400000, 0.700000, 0.039124, 40.000000
	Synaptics Edge Motion Pressure (292):	14, 79
	Synaptics Edge Motion Speed (293):	1, 102
	Synaptics Edge Motion Always (294):	0
	Synaptics Button Scrolling (295):	1, 1
	Synaptics Button Scrolling Repeat (296):	1, 1
	Synaptics Button Scrolling Time (297):	100
	Synaptics Off (298):	0
	Synaptics Guestmouse Off (299):	0
	Synaptics Locked Drags (300):	0
	Synaptics Locked Drags Timeout (301):	5000
	Synaptics Tap Action (302):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (303):	1, 1, 1
	Synaptics Circular Scrolling (304):	0
	Synaptics Circular Scrolling Distance (305):	0.010000
	Synaptics Circular Scrolling Trigger (306):	2
	Synaptics Circular Pad (307):	0
	Synaptics Palm Detection (308):	0
	Synaptics Palm Dimensions (309):	10, 99
	Synaptics Coasting Speed (310):	0.000000
	Synaptics Pressure Motion (311):	14, 79
	Synaptics Pressure Motion Factor (312):	1.000000, 1.000000
	Synaptics Grab Event Device (313):	1
	Synaptics Gestures (314):	1
	Synaptics Capabilities (315):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (316):	1, 1
	Synaptics Area (317):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (318):	0
```

---

### Post by Delvien on 2010-05-04
Same problem here.

---

### Post by FireNoodle on 2010-05-15
This should fix the scrolling:
> Add the following to /etc/modprobe.d/psmouse.conf:
options psmouse proto=imps

The psmouse.conf file doesn't exist by default, just create a text file with that name in /etc/modprobe.d/

After that just stop/restart the touchpad with:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

from comment #78: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)

---

### Post by knifesk on 2010-05-18
it works great for vertical scrolling!! but not for horizontal :(

any suggestion?

---

### Post by scubajeff on 2010-05-23
FireNoodle's fix make the touchpad disappear from "xinput -list", and thus lost the chances to activate those lovely features like two fingers scroll, circular scroll etc. the worst thing is it bring back the accidentally click while typing issue.

When I use 5.04 on my sony, it already had the issue with Alps touchpad, and now it's 10.04, bug still existed. It's a shame!

---

### Post by ComputerJy on 2011-04-18
> **FireNoodle said:**
> This should fix the scrolling:


After that just stop/restart the touchpad with:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

from comment #78: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)
Thanks, I've been looking for this fix for hours

---

### Post by Lamukra on 2011-08-31
> **FireNoodle said:**
> [SIZE="2"][SIZE="1"]This should fix the scrolling:


After that just stop/restart the touchpad with:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

from comment #78: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)[/SIZE][/SIZE]


That is amazing...
I spent so much time on figuring out how to fix this issue...
Using Sony Vaio with Ubuntu 11.04 and Classic GUI

Thank you so much!!!

> [SIZE="3"]Update 1:[/SIZE]

After doing this ALPS is no longer detected in the system
log from devices:
```
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse2 event8 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
```

Log from Xorg:
```
[    29.177] (II) Using input driver 'synaptics' for 'Alps Touchpad'
[    29.177] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.177] (**) Option "SendCoreEvents"
[    29.177] (**) Alps Touchpad: always reports core events
[    29.177] (**) Option "Device" "/dev/input/event8"
[    29.470] (**) Option "SHMConfig" "true"
[    29.470] (--) Alps Touchpad: invalid x-axis range.  defaulting to 1615 - 5685
[    29.470] (--) Alps Touchpad: invalid y-axis range.  defaulting to 1729 - 4171
[    29.470] (--) Alps Touchpad: invalid pressure range.  defaulting to 0 - 256
[    29.470] (--) Alps Touchpad: invalid finger width range.  defaulting to 0 - 16
[    29.470] (**) Option "HorizEdgeScroll" "0"
[    29.780] (--) Alps Touchpad: no supported touchpad found
[    29.780] (EE) Alps Touchpad Unable to query/initialize Synaptics hardware.
[    29.880] (EE) PreInit returned 11 for "Alps Touchpad"
[    29.880] (II) UnloadModule: "synaptics"
[    29.880] (II) Unloading synaptics
```

Xorg.conf Input Device Section
```
Section "InputDevice"
	Identifier "Alps Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/event8"
	Option "Protocol" "auto-dev"
	Option "HorizEdgeScroll" "0"
	Option "SHMConfig" "true"
EndSection
```

---

