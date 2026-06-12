---
title: "games wont load GLX wont work"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by poloking on 2007-06-13
When I try to load up 3d games my computer will not allow it.

The screen flashes then it comes up with this dialogue box:
Code:
Could not set videomode:
Couldn't find matching GLX visual
Please help I do not know what to do about it.

Dont know if it has anything to do with it but desktop effects wont work either they say :
Code:
Desktop effects could not be be enabled
Thanks alot in advance

Rob

---

### Post by Nythain on 2007-06-13
do you have the proprietary drivers for your video card installed and set up properly

what video card do you have?
results of
```

glxinfo | grep render

```
and finally, the contents of your /etc/X11/xorg.conf

---

### Post by poloking on 2007-06-13
To tell you the truth i dont know what drivers I have installed it took me a while to get gdm to actually load, so i changed alot. I have an nvidia GEFORCE FX 5200


```
glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```


and contents of my xorg.conf:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200LE]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CMC 17"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200LE]"
	Monitor		"CMC 17"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


thanks

---

### Post by hikaricore on 2007-06-13
There's your problem, you're using the vesa driver. You'll never get 3d accel on the vesa driver.  >.<

You need to see if your card is supported by any of the community or nvidia released binary drivers.

---

### Post by poloking on 2007-06-13
How do i do that

---

### Post by dave091 on 2007-06-13
> **poloking said:**
> How do i do that

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by poloking on 2007-06-16
I did all of that and it came up with an error message saying that the xserver and my driver had a different version number or something like that.

and so the xserver coiuldnt start

---

