---
title: "Dual monitor on Compaq 6710b Laptop"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by mannie.p on 2008-04-02
Somebody might give or help build xorg.conf for dual monitor support on a Compaq laptop 6710b?

Ubuntu Gutsy Gibbon

Thank you

---

### Post by nandinga on 2008-07-18
Yep, I have the same problem with this same laptop. I was using it dual headed (laptop monitor + LCD 1280x1024) until a recent update broke it.

It was cool because it somehow knew when I was having the other monitor plugged and gave me correct configuration plugged or not. Strange though that this adjustment was only effective once I was graphically logged in... I mean, e.g when I had the extra mon plugged, my gdm login page was mirrored on both mons, but once I logged in it just adjusted itself. Maybe xrandr involved somewhere there?

This was my xorg.conf (it worked, but stopped working yesterday).

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual 3072 3072
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Try it, it may work for you.

On the other side, can anyone help me on this issue also? Right now with this config I get the image mirrored on both monitors, using the resolution of the big one (the extra LCD: 1280x1024).

Thank you all!

---

