---
title: "aiglx, compiz on Toshiba tecra 8100"
date: 2007-10-28
forum: Desktop Environments
---

### Post by dewatech on 2007-10-28
Hi..

I have problem with compiz on my age Toshiba Tecra 8100. I am using Ubuntu 7.10. My VGA Card is S3 Savage MX (8M) with 256MB of  Memory. When I try to change the Desktop Effect it says that it cannot be run. Tried **glxinfo | grep direct** and the result: **direct rendering - yes**, but **grep -i aiglx /var/log/Xorg.0.log** give me results:

```
(**) Option "AIGLX" "true"
(**) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
```

Try to run compiz:  **compiz.real  --replace**

```
compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

The xorg.conf :

```
Section "Files"
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "extmod"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri"
EndSection

Section "DRI"
    Mode 0666
    Group 0
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
	Identifier	"S3 Inc. 86C270-294 Savage/MX-MV"
	Driver		"savage"
            VideoRam 8192
            Option "DPMS"
            Option "AGPMode" "2"
            Option "DRI" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86C270-294 Savage/MX-MV"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    Option "AIGLX" "true"
    Screen "screen1"
EndSection
```

Could some one help me please..

---

### Post by dewatech on 2007-10-28
I am Sorry..
First posting here
Wrong **Support Categories**  :)
Must be in **Desktop Effects & Customization**  
But still need help.. :) or maybe admin help me to move this posting to **Desktop Effects & Customization**  thread.. :) :)

---

