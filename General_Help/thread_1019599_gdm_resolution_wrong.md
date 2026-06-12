---
title: "gdm resolution wrong"
date: 2008-12-23
forum: General Help
---

### Post by rick71 on 2008-12-23
After I installed an FX5200 video card (an enabled the nvidia driver) the gdm screen resolution is wrong. The gdm screen is too big an looks like the the top left corner is aligned as it should be, with the right side and bottom off screen. This has the effect of cropping the actions menus im many gdm screens, and the login input windows in others.

Does anyone know how I might fix this?

---

### Post by dcstar on 2008-12-23
> **rick71 said:**
> After I installed an FX5200 video card (an enabled the nvidia driver) the gdm screen resolution is wrong. The gdm screen is too big an looks like the the top left corner is aligned as it should be, with the right side and bottom off screen. This has the effect of cropping the actions menus im many gdm screens, and the login input windows in others.

Does anyone know how I might fix this?

System-Preferences-Screen Resolution

---

### Post by rick71 on 2008-12-23
> **dcstar said:**
> System-Preferences-Screen Resolution

I tried that, it will reset the resolution of the user desktop, but not gdm.

---

### Post by dcstar on 2008-12-24
> **rick71 said:**
> I tried that, it will reset the resolution of the user desktop, but not gdm.

Check the /etc/X11/xorg.conf file and see if there is an incorrect resolution set in it.

---

### Post by mättu on 2008-12-26
screen resoltion no longer in /etc/X11/xorg.conf, it seems.

Sadly I have not yet found any information about how and where it is stored..

---

### Post by dcstar on 2008-12-26
> **mättu said:**
> screen resoltion no longer in /etc/X11/xorg.conf, it seems.

Sadly I have not yet found any information about how and where it is stored..

Try this option in the xorg.conf file:

```
Section "Screen"
........
**    Option         "UseEdidDpi" "False"**
........
EndSection
```

Or replace the 

```
    SubSection     "Display"
        Depth       24
**        Modes      "nvidia-auto-select"**
    EndSubSection
```

with:

```
    SubSection     "Display"
        Depth       24
**        Modes      "1680x1050"**
    EndSubSection
```

and see what happens (replace the 1680x1050 with whatever your screen actually is).

---

### Post by mättu on 2008-12-26
thanks for your advice. My xorg.conf, anyhow:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
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

### Post by rick71 on 2008-12-27
I did a dpkg-reconfigure of xorg. The resoluion problem seems to have been fixed

---

### Post by dcstar on 2008-12-27
> **rick71 said:**
> I did a dpkg-reconfigure of xorg. The resoluion problem seems to have been fixed

See what your xorg.conf looks like now.......

---

