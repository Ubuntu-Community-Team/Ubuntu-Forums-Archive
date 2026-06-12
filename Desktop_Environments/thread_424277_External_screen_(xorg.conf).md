---
title: "External screen (xorg.conf)"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Re-JeeP on 2007-04-26
Hi!

I'm trying to connect an external screen to my laptop.

With my **xorg.conf** as I have now the resolution on the screens will be the same.
I want to have **1366x768** on my laptop and **1680x1050** on my external screen.

I would really appreciate if someone could help me out!

```
Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/100dpi/"
	FontPath     "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
	Load  "xtrap"
	Load  "dri"
	Load  "glx"
	Load  "freetype"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard"
	Driver      "kbd"
	Option	    "XkbModel"	"pc105"
	Option	    "XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier  "Mouse"
	Driver      "mouse"
	Option	    "Protocol" 		"auto"
	Option	    "Device" 		"/dev/input/mice"
	Option	    "ZAxisMapping" 	"4 5"
EndSection

Section "Monitor"
	Identifier   "Default Monitor"
	Option       "DPMS"
EndSection

Section "Monitor"
	Identifier		"External Monitor"
	#HorizSync       from-to
	#VertRefresh     from-to
	Option          "DPMS"
EndSection

Section "Device"
	Identifier  "GMA 900"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "MonitorLayout" "CRT,LFP"
	Option      "Clone" "On"
	Option      "DevicePresence" "yes"
	Option	    "MetaModes" "1366x768,1680x1050;"
	Option 		"TwinView" "1"
EndSection
       
Section "Screen"
	Identifier 	"Default Screen"
	Device     	"GMA 900"
	Monitor    	"Default Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1366x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device	"GMA 900"
	Monitor	"External Monitor"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Mouse"	"CorePointer"
	InputDevice	"Keyboard"	"CoreKeyboard"
EndSection

Section "ServerLayout"
	Identifier	"Extra Layout"
	Screen		"External Screen"
	InputDevice	"Mouse"		"CorePointer"
	InputDevice	"Keyboard"	"CoreKeyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

