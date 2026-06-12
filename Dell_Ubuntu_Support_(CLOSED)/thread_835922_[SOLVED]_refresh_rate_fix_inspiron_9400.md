---
title: "[SOLVED] refresh rate fix inspiron 9400"
date: 2008-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FranciscoLopez on 2008-06-20
ok i installed 8.04 like last month and my display is flickering ocasionally, now i think this is due to the refresh rate being 50hz while in xp i got a minimun of 60hz, on the native 1920x1200 resolution, and better on lower resolution, now I think this is my xorg.conf which ive read if i modify i might fix. here it is:

"
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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection"


now how can i fix my refresh rate?

---

### Post by mtbsoft on 2008-06-24
I have the same laptop but I'm using the restricted drivers (fglrx) which seem to give me the 60Hz no problem.

You shouldn't need to hand modify the xorg file, just enable the restricted drivers - there's nothing in mine that specifically deal with frequency.

---

### Post by FranciscoLopez on 2008-06-25
hmmm thanx for the response but i am actually using the restricted nvidia drivers. 

now it seems i fixed it by installing from synaptic a package called
"nvidia-settings", from then on it gave me  the 60hz refresh and the flickering stopped.

---

