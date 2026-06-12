---
title: "GLScreensavers:libGL warning"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Barnaby on 2005-12-05
Every time I try to access the  3d screensavers they do not preview or work.
Error message: "libGL warning: 3d driver claims to not support visual .." and then certain sizes at the end like "0x24", "0x28".
There was a similar problem on a Vectorlinux system I had when trying to run Wine.

Now, all this wouldn't be too astonishing considering I do not have proper drivers installed, BUT i thought it was said 3d support for older ATI grfx cards is already built in?

I have a ATI Rage Pro/PF 32MB with TV out (but do not intend to use TV out).
Roughly from late 99/2000 production.

Are there proper Linux drivers around for these cards?

Barnaby (Ubuntu 5.10, 32bit, 1000MHz AMD Duron OC, 512Ram)

---

### Post by kosmic on 2005-12-05
have a look at [https://wiki.ubuntu.com/BinaryDriverHowto]("https://wiki.ubuntu.com/BinaryDriverHowto")
 
But your card should already have aceleration suported.

---

### Post by Barnaby on 2005-12-05
Thanks, looks like it should work but doesn't, not only in Ubuntu. Maybe s'thing special about this TV out card?
Anyway, will try the fglrx driver, will it be any good for this?

Barnaby

---

### Post by Barnaby on 2005-12-05
Thought this might give somebody a clue: xorg.conf


Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"JC-17W41"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Monitor		"JC-17W41"
	DefaultDepth	24

---

