---
title: "X11 Cursor invisible"
date: 2009-02-02
forum: General Help
---

### Post by Cobra_Fast on 2009-02-02
Hey guys,

today i played around with my xorg.conf and kernel today to get 3D accelleration working with dual-head...
now on my left screen i have no cursor visible, on the right screen its a white square.
I already played around with options like "SWCursor" and "HWCursor" in several sections with no effect.

There's my Xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "aticonfig-Screen[1]" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "SwapScreens" "off"
	#Option	    "SWCursor"	  "True"
	Option	    "HWCursor"	  "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth	24
		Virtual 1280	1024
		Modes	"1280x1024@85"	"1280x1024@80"
		#Option	"HWCursor"	"off"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		#Viewport   0 0
		Depth     24
		Modes	"1280x1024@60"
		#Option	"HWCursor"	"off"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
	Option		"AIGLX"		"off"
EndSection

```
and btw. i only get Mesa running (no direct rendering) but the cursor problem is more important.

---

