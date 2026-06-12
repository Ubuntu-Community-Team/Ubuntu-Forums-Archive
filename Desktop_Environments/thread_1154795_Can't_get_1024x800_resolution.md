---
title: "Can't get 1024x800 resolution"
date: 2009-05-10
forum: Desktop Environments
---

### Post by PIHKAL on 2009-05-10
I've just installed Ubuntu (Hardy) on my laptop, and I'm having some trouble getting the right resolution. It was running fine at 1024x800 when I first installed, but then I hooked up my TV as an external monitor to watch a film, and now I can only get 1024x768.

Does anybody know how to fix this?

---

### Post by overdrank on 2009-05-10
> **PIHKAL said:**
> I've just installed Ubuntu (Hardy) on my laptop, and I'm having some trouble getting the right resolution. It was running fine at 1024x800 when I first installed, but then I hooked up my TV as an external monitor to watch a film, and now I can only get 1024x768.

Does anybody know how to fix this?

Hi and with Hardy 8.04 You may either use recovery mode and run xfix or use the command with the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by PIHKAL on 2009-05-10
Thanks for the reply

I just tried running xfix, but to no avail, and the displayconfig-gtk menu was only letting me choose between the same resolutions as the screen resolution menu (640x480, 800x600, 1024x768, 1280x768 & 1280x800).

Any more ideas anybody?

---

### Post by PIHKAL on 2009-05-10
Btw, here's my xorg.conf if it helps:
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
EndSection

---

