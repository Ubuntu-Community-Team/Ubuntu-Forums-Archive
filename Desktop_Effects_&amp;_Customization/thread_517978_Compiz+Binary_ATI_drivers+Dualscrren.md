---
title: "Compiz+Binary ATI drivers+Dualscrren?"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by mr-bean on 2007-08-05
Has anyone had any success with that setup?

I can get compiz-fusion running ok on one screen (or same image on both screens)
I can get xinerama to work on both screens if I login to a NON xgl session. (No Compiz)
I can get Big Desktop to work on both screens, again only in a NON xgl session. (No compiz)

I just cant get both monitors running when using compiz-fusion (xgl session).

The best I've had is:  Left monitor running compiz-fusion all 3D effects working, and the right monitor was black, but running, I could move the mouse pointer into that monitor, and the pointer changed to a black X with white outline, but there was no desktop display.

I'm running Ubuntu 7.04 x64
ATI x550 with binary drivers
2 x 22" monitors (1680x1050), one DVI, one analog.

I'm getting an Nvidia 6800GT dual DVI card soon. Has anyone had any success with that card?

Thanks.
Regards, Mr-Bean...

---

### Post by Buzbe on 2007-08-05
I've managed to get both working with XGL and FGLRX, but my gnome menu bars are stretched across both screens.

Very annoying.

For my xorg.conf please see my other post.

Jon

---

### Post by mr-bean on 2007-08-05
Thanks Buzbe.  I'll give that a go shortly.
Funny how you can search the forum for days and miss a post like that.

I'll let you know how it goes.

It looks from your xorg.conf that you aren't running Dual Head, but "Big Desktop".

but hey, if that works I'll take that.

Thanks for the help....

---

### Post by mr-bean on 2007-08-05
Well I tried and tried....
Still no further forward with this.

Buzbe, I used your xorg.conf as a guide, and got what you see in the first pic.  Looks Cloned and corrupted.  :-(

The other 2 pics show where I am at the minute.

Cube picture:
Compiz-fusion running on one monitor.

Login picture:
The login screen where you can see the mouse pointer on the second monitor.  Seems like the X-server is running, but with no window manager on that display...  Weird?

Bye bye ATI, gonna get me a Nvidia card.
:guitar:

---

### Post by jpereira on 2007-08-06
Hi there,

I have this working on my ATI X700, with Xgl and compiz, laptop resolution at 1280x800 and external screen at 1024x768. Drawback is that pressing menus becomes pretty slow. Here's a copy of my xorg.conf:
```


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Laptop Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"glx"
	Load		"v4l"
	Load		"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"150"
	Option		"RightEdge"	"1070"
	Option		"TopEdge"	"100"
	Option		"BottomEdge"	"310"
	Option		"FingerLow"	"25"
	Option		"FingerHigh"	"30"
	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"220"
	Option		"MaxDoubleTapTime"	"180"
	Option		"HorizEdgeScroll"	"0"
	Option		"VertEdgeScroll"	"0"
	Option		"TapButton1"	"0"
	Option		"TapButton2"	"0"
	Option		"TapButton3"	"0"
	Option		"LockedDrags"	"off"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"50"
	Option		"VertTwoFingerScroll"	"1"
	Option		"HorizTwoFingerScroll"	"1"
        Option          "MinSpeed"      "0.15"
        Option          "MaxSpeed"      "0.90"
        Option          "AccelFactor"   "0.10"
	Option		"Emulate3Buttons"	"false"
	Option		"SHMConfig"	"on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI X700"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"

	Option	"VideoOverlay"		"on"
	Option	"OpenGLOverlay"		"off"
	Option	"Capabilities"		"0x00000800"

	Option	"MonitorLayout"		"LVMS,AUTO"
	Option	"DesktopSetup"		"horizontal"
	Option	"PairMode" 		"1280x1024+1024x768"
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"ATI X700"
	Monitor		"Laptop Monitor"
	Defaultdepth	24

	SubSection "Display"
		Depth	1
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1400x1050" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"0"
EndSection

```

---

### Post by mr-bean on 2007-08-07
Thanks for the info jpereira,  I'll backup my xorg.conf and give your settings a go.
"LVMS" is a new one on me though?

Option "MonitorLayout"	"LVMS,AUTO"

I'm not too sure what to use in the line above.
I would think "CRT1,LVDS" would be the way to go from what I've been reading, even though I've got two LCD's.  Not too sure on that one so will have to experiment.

I'm getting better at using Ubuntu and Linux in general.  I even built aMSN from soucres, and it works....

:guitar:

Thanks for all the info so far guys....  Hopefully I'll get there soon.

Regards,  Mr-Bean...

---

