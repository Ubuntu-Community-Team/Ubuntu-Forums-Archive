---
title: "xfce problem"
date: 2007-01-23
forum: Desktop Environments
---

### Post by ZippidyDoo on 2007-01-23
I just upgraded to the new xfce 4.4.0.  Install worked and everything seems fine except I don't have the Compositor tab in my "Window Manager Tweaks".  Was there something I should of installed or missed? Anyone else out there with the same issue? I appreciate any help possible :)

---

### Post by Wight_Rhino on 2007-01-23
There's a Checkbox to enable the compositor IIRC. I can't give specific directions right now, (I'm on Windows at work:( ) But I think it's in the window manager box somewhere.

Take a look around.

---

### Post by K.Mandla on 2007-01-23
> **ZippidyDoo said:**
> I just upgraded to the new xfce 4.4.0.  Install worked and everything seems fine except I don't have the Compositor tab in my "Window Manager Tweaks".  Was there something I should of installed or missed? Anyone else out there with the same issue? I appreciate any help possible :)
Do you need to enable compositing in your xorg.conf file? Perhaps that has changed with 4.4.0.

---

### Post by ZippidyDoo on 2007-01-23
Aaah, yes that was it K.Mandla, thanks. Problem now is that totally messed up my desktop, lol!  It looked like my screen is on acid with some beautiful transparent panels and slow motion reactions... soo I had to disable compositor :( I believe my ati card has failed me once again. Darn the fglrx. Now any suggestions on what'll fix that problem? xD

---

### Post by lien_meat on 2007-02-17
ZippidyDoo,  could you tell me exactly what you added to your xorg.conf to enable compositor?  I'm having the SAME EXACT problem and I've followed lots of guides and messed with my xorg.conf quite a bit.

Here is my current xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GEFORCE go 6150"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option "RenderAccel" "true"
 	Option "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GEFORCE go 6150"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
   Option "Composite" "Enable"
 EndSection

```

Thanks for any help you guys!

---

