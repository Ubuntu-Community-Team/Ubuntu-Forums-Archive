---
title: "XServer restarts with CompositeExt."
date: 2006-07-19
forum: Desktop Environments
---

### Post by ellion on 2006-07-19
Hi there,

I finally managed to get 3D Support with the radeon-driver on my ThinkPad T30  with an ATI Radeon Mobility 7500. Now I wanted to use AIGLX, due to performance and that little applet. 
The Problem now is: When I enable the Composite Extension for Xorg the XServer restarts after login. I'm pretty sure that this is because of compiz or OpenGL respectively. When starting X without compiz it starts like a charm, but restarts when starting an GL app, glxgears for example. Commenting out the Composite Section keeps X running.

The Xorg.0.log and dmesg leave me without any explicit error.

Not too sure, if it's necessary, but I'll post my Xorg.conf. Oh, and it's a Radeon 7500 Mobility, even if X says 9000:

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
	Load	"dbe"
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
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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
EndSection


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "radeon"
	BusID		"PCI:1:0:0"
	Option "sw_cursor"
	Option "RenderAccel" "true"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "True"
	Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"	"true"	
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option	"Composite"	"Enable"
#EndSection


```


I'm open for any ideas!

Thanks in advance



PS: Hope it's the right forum, wasn't too sure :/

---

### Post by philippe_carlo on 2006-07-19
Please, read the HOWTOs. You need to set up the fglrx drivers for Xorg first, I think. Here are some links:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")
[http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")
[http://www.ailis.de/~k/docs/atilinux/]("http://www.ailis.de/~k/docs/atilinux/")

---

### Post by ellion on 2006-07-19
fglrx isn't working with 7500. I think it supports something like 8500 and higher. radeon should do fine, I guess, doesn't it?

---

### Post by finalbeta on 2006-07-19
This comes from the opensuse site for XGL, perhaps it helps:

Common configuration errors

    * Xgl does not need the Composite extension enabled in xorg.conf - in fact this is counter-productive, as e.g. the NVIDIA driver disables OpenGL by default when Composite is enabled. The Composite extension is provided by Xgl itself, without the need to configure anything.
      If you get an error about missing Composite extension when starting compiz, you probably tried to start it on the base Xorg server (which shouldn't be used for any program any more except for starting Xgl itself) and not on the Xgl server. Set your DISPLAY variable accordingly.

---

### Post by ellion on 2006-07-19
Thanks, at least it leaves me the option to use XGL, nonetheless I would prefer AIGLX.

Anyone knows if that systray program AIGLX ships with works for XGL? For my laptop it would be fine to easily turn off compiz due to battery and heat. On my desktop PC I just defined two servers for gdm which I can switch on login, but a systray program would be easier :)

---

### Post by rafalr on 2006-08-08
finalbeta,

How/where to set the Display properly ?

rafal

---

