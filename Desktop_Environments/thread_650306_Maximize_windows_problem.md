---
title: "Maximize windows problem"
date: 2007-12-26
forum: Desktop Environments
---

### Post by Reeva on 2007-12-26
Hello,

I have a problem maximizing my windows.

I have a 14.1" HP notebook with an 19" TFT connected for use as Main monitor.

Now the 19" has a resolution of 1024x1280, and everything works fine. Except when I maximize my windows, the width is maximized, but not the hight. It maximizes to the height of my notebook display.

How can I force it to maximize my whole screen?

Thank you at advance
R.

---

### Post by lisati on 2007-12-26
Pressing F11 might help..... feel free to let us know how you get on.

---

### Post by as0l0 on 2007-12-26
F11 - nice tip, thankyou.

---

### Post by Reeva on 2007-12-26
Hello,

No F11 doesn't work. Only in Firefox, where I get a fullscreen browser then ..

But when I want to maximize a normal window, it goes to half of the screen in height.

---

### Post by Reeva on 2007-12-26
Still got the same problem .. seems like Gnome doesn't use the 19" as main monitor or something ..

Can I force that?

---

### Post by Reeva on 2007-12-27
This is my xorg.conf file:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1951"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Acer AL1951"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

```

---

### Post by tsung_cheng on 2008-01-09
i have the same problem ... :(

anyone help?

---

