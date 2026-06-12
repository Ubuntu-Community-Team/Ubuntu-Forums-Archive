---
title: "Dell 600m w/ external Xorg.conf Help"
date: 2008-02-15
forum: Dell  Ubuntu Support
---

### Post by sbartz on 2008-02-15
Here's my hardware.
Dell Inispiron 600m
Screen
1400x1050
ViewSonic  VA1930wm
1440x900 (Widescreen)

I bought the external because the laptop monitor was on the fritz.

What I'm trying to do:
Have the external be the "primary" monitor.
I want full screen windows on the external to not be bigger than the monitor.
The laptop screen should just display what's on the external. I don't care if it leaves off pixels or doesn't fill the top and bottom of the screen.

I found some xorg.conf help in another thread. I feel like I'm close just not finished.
What should I change?
Thanks for your help.

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"MonitorLayout"	"CRT,LFP"
EndSection

Section "Device"
	Identifier	"Device1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"Clone" "on"
	Screen		0
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	HorizSync 28-72
	VertRefresh 43-60
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	HorizSync 30-83
	VertRefresh 56-75
	Modeline "1440x900@60" 106.5 1440 1520 1672  1904 900 903 909 934
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
	Depth 24
	Modes "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device		"Device1"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
	Depth 24
	Modes "1440x900@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Layout"
	Screen "External Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by sbartz on 2008-02-15
Is this the right section for this post? If not please move it to a more appropriate section. Thanks.

---

