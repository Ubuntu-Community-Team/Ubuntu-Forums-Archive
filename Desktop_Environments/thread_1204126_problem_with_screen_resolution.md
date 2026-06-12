---
title: "problem with screen resolution"
date: 2009-07-04
forum: Desktop Environments
---

### Post by nagaraja on 2009-07-04
hi,

I m using Nvidia fx5500 graphics card.in hardware drivers it says that graphics card is enable and it is in use. but i cant increase my screen resolution. It has only two options 800x600 and 640x420, my graphics card can support 1024x768 mode in windows .. my xorg.conf file is like
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

i have tried with envyng but its not working .. compiz is also not working.While booting up it always prompt to run in Low graphics mode.

plz help me

---

### Post by karrank% on 2009-07-04
Have you gone into system>administration>hardware drivers to enable the proprietary nvidia drivers?

---

