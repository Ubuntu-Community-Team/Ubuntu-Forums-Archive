---
title: "xorg.conf monitor names with Dell D/Port and nVidia"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Meson on 2008-04-23
What are the monitor names (for use with the "ConnectedMonitor" and "UseDisplayDevice" options) in xorg.conf?

I'm pretty sure the DVI port on the docking station is DFP-1.  What is the VGA port on the docking station, the VGA port on the laptop itself, and the built-in monitor (is it a DFP or CRT?)

I've got a Dell D/Port docking station, Latitude D800 laptop, and nVidia GeForce FX go5650 video card.  My external monitor is attached to the DVI port on the docking station.

---

### Post by Ph0N37Ic5 on 2008-04-26
The internal display is probably DFP-0, the VGA port both for the one on the laptop and the one on the docking station would be CRT-0 I think but I might be wrong here, it just seems to be the way on my laptop (Precition M60 with D/Port Docking), the DVI port on the docking would be DFP-1, and if you have TV out it would be TV-0.

Having a look around the net seems to suggest that the Option "UseDisplayDevice" needs only "DFP" or "CRT" or "TV" and that it belongs in the Device section, although a more logical position for it would be in the Monitor section.

---

### Post by Meson on 2008-04-26
Well, what actually gave me the behavior I wanted is this:
```
	Option		"UseDisplayDevice" "DFP-1, CRT"
```

When my laptop is on its own, and it boots up, the built-in monitor is used.  When it's in the dock, the external DVI-connected monitor is used.  I no longer have to manually change my xorg.conf file depending on location.

My original setup was "ConnectedMonitor" "DFP-1, DFP-0", but that seemed to stop working at some point (between installs).

I'm actually settings these options in the "Screen" section.  I remember reading at one point that anything that can be set in "Device" can be placed in "Screen"

```
Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
EndSection

Section "ServerLayout"
	Identifier	"monoLayout"
	Screen		"monoScreen"
	Option		"Xinerama" "false"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "Synaptics Touchpad" "CorePointer"
EndSection
Section "Device"
	Identifier	"monoDevice"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
Section "Monitor"
	Identifier	"monoMonitor"
	Option		"DPMS" "true"
EndSection
Section "Screen"
	Identifier	"monoScreen"
	Device		"monoDevice"
	Monitor		"monoMonitor"
	#Option		"ConnectedMonitor" "DFP-1, DFP-0"
	Option		"UseDisplayDevice" "DFP-1, CRT"
	Option		"MetaModes" "nvidia-auto-select"
	Option		"AllowGLXWithComposite" "True"
	Option		"RenderAccel" "True"
	Option		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection     "Display"
		Depth       24
	EndSubSection
EndSection
```

---

### Post by stults on 2009-11-20
Thank you so much for this info!

I have a Dell Latitude D800 that had the light go out on the LCD screen.  So in order to be able to use it I wanted to hook it up to an external monitor.  By adding the line "Option  "UseDisplayDevice" "CRT"" to the Device section of the Xorg.conf (/etc/X11/xorg.conf), it used the external monitor immediately when it boots.  Now I can still get some use out this system without blowing all the money on a new display!

---

