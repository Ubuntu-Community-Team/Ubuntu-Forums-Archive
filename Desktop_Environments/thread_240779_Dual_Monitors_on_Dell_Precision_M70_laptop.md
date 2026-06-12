---
title: "Dual Monitors on Dell Precision M70 laptop"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Vylar on 2006-08-21
I'm having some problems configuring dual monitors on a Dell Precision M70 laptop.

My setup:
[list]
[*]Machine: Dell Precision M70 laptop contected to a docking station
[*]Videocard: nVidia Quadro FX Go1400
[*]Monitor 1: Dell 1905FP 19" LCD monitor connected via the docking station's DVI port
[*]Monitor 2: Dell 1905FP 19" LCD monitor connected via the docking station's VGA port
[/list]

My problem: I've followed the [how-to]("http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html"), and it seems to work, except the second monitor does seem to be getting a signal.  With some messing around, I can get one or the other monitors working, but not both at the same time.  X seems to think there are two monitors attached, because I can take a screenshot in Gnome and it shows an extended desktop with stuff that should be displayed on the second monitor.  I read through the forums, and I noticed that quite a few people resolve this problem by setting the screen resolution in Gnome to 2560x1024, but mine is already set to that and it doesn't solve the problem.  I was able to get the dual monitors to work in Fedora Core 4 and Windows XP with no trouble, so I know they are connected correctly and work.

Here's the relevant sections of my xorg.conf file:
```


Section "Device"
	Identifier	"NVIDIA Corporation NV41 [Quadro FX Go1400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "2"
	Option		"NoLogo" "1"
	Option		"RenderAccel" "1"
	Option		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	#Option		"ConnectedMonitor" "dfp, crt"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option 		"Metamodes" "1280x1024,1280x1024; 1920x1200,null"
	#Option		"SecondMonitorHorizSync" "31.5-67.0"
	#Option		"SecondMonitorVertRefresh" "50.0-75.0"
	#Option		"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync    31.5 - 67.0
	#VertRefresh  50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41 [Quadro FX Go1400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		1 
		Modes		"1920x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1920x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1920x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15 
		Modes		"1920x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1920x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1920x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "off"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

Any help would be greatly appreciated!

---

### Post by Vylar on 2006-08-21
UPDATE: After another hour of playing around with it, I figured out what the problem is.  For anyone else who might have this same problem, here is the solution:

I connected the laptop to a projector, which plugged directly into the laptop's external VGA port, and everything worked fine.  So I decided to change this line:

```
Option		"ConnectedMonitor" "dfp, crt"
```

To:

```
Option		"ConnectedMonitor" "dfp-1, crt-0"
```

And now everything works perfectly.

---

### Post by TheMono on 2006-08-21
Clever - glad you got it working!

---

