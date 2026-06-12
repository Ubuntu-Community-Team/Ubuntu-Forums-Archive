---
title: "Gutsy killed X 1420n (Intel X3100)"
date: 2007-10-22
forum: Dell  Ubuntu Support
---

### Post by oddabe19 on 2007-10-22
Hey guys,
So I upgraded to gutsy, through their gtksu update-manager -c.

Anyway, now I can't start X.

The error is I810: No matching Device section for instance.

The screen is one of the 1400x900 displays, but with the intel X3100 card

Thanks

---

### Post by sciurus on 2007-10-28
Try this /etc/X11/xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
```

If you ever want to hook your laptop up to another monitor, change the 'Virtual 1440 900' line to reflect the highest resolution you will use. For example, if you were going to use your built-in screen and another WXGA+ monitor side by side, it should be 'Virtual 2880 900'. You can use the intel's grandr utility (sudo aptitude install grandr) to easily extend, arrange, and rotate displays.

---

