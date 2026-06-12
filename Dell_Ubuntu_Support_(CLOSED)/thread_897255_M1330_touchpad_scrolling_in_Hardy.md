---
title: "M1330 touchpad scrolling in Hardy"
date: 2008-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-08-22
I've noticed that under Vista, the touchpad's virtual scrollbars work on my M1330 laptop.  (Sliding one's finger along the right edge and the bottom edge of the touchpad causes scrolling in the vertical and horizontal directions, respectively.)  But under the generic 8.04 Ubuntu, they don't work.  Do they work under the pre-installed Ubuntu 8.04 from Dell?  If so, would you please list the contents of the touchpad section of your /etc/X11/xorg.conf file?

*TimDaniels*

---

### Post by Technoviking on 2008-08-22
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"1900"
	Option		"RightEdge"	"5000"
	Option		"TopEdge"	"1400"
	Option		"BottomEdge"	"4500"
	Option		"FingerLow"	"25"
	Option		"FingerHigh"	"35"
	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"220"
	Option		"ClickTime"	"0"
	Option		"VertEdgeScroll"	"1"
	Option		"VertScrollDelta"	"45"
	Option		"HorizEdgeScroll"	"1"
	Option		"HorizScrollDelta"	"45"
	Option		"MinSpeed"	"0.08"
	Option		"MaxSpeed"	"0.60"
	Option		"AccelFactor"	"0.003"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"TapButton1"	"1"
	Option		"TapButton2"	"3"
	Option		"TapButton3"	"2"
	Option		"SHMConfig"	"on"
EndSection
```

---

### Post by adult swim on 2008-08-22
after doing what mike suggested i had to add my touchpad to the server layout at the end of xorg.conf
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by TimDaniels on 2008-08-23
Thanks, guys.  I found that I could leave out everything in the "Synaptics Touchpad" section of xorg.conf from LeftEdge all the way to the end of the section, and the GUI at **System | Preferences | Mouse** would control all the parameters.  And specifically, that GUI (in the **Touchpad tab** would override VertEdgeScroll and HorizEdgeScroll.  So, the only Option lines that I have in the "Synaptics Touchpad" section now are SendCoreEvents, Device, and Protocol - everyting else is set in the **Mouse** GUI, including scrolling.

*TimDaniels*

---

### Post by greenpeace on 2008-10-04
hi guys, does anyone know how to enable two-fingered scrolling on a m1330 running Hardy?  I've checked other threads, but can't get it to work.

I've added the two lines suggested, 

    Option         "VertTwoFingerScroll"   "1"
    Option         "HorizTwoFingerScroll"  "1"

but I've found that when i run

sudo dpkg-reconfigure -phigh xserver-xorg

It throws the error:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081004130229

so something's clearly not right... anyone got any pointers?

---

