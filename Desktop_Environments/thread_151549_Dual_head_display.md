---
title: "Dual head display?"
date: 2006-03-28
forum: Desktop Environments
---

### Post by erlyrisa on 2006-03-28
Dual head diaplays are great - and especially configurable with Xorg/Xfree.
-but I was wondering has any-one ever been able to set it up to be able to move program windows from one display to another? you know the way windows does it (I think they just may the desktop the size of both of the monitors)

-is there a way to setup .conf to have the large desktop or is there anyway to tell windows to stick themselves to other displays (when theyre already open instead of the commandline --display :00 switch)

anyway I'm not fussed if I never find a way of doing this - but I am pretty sure it is possible - b/c I have seen linux in TV shows doing things like displaying an image over an array of displays.

---

### Post by erlyrisa on 2006-03-28
-actually I'll add another sub note to this --
is there a way to assign a shortcut key to switch displays - youknow like switching workspaces.

---

### Post by snaga on 2006-03-28
My two displays act as one, allowing me to just drag windows back and forth. The only way I know of to control where a window comes up in is to put the cursor there when the program is launching.

Here's my xorg.conf, if that helps. I'm using twinview.

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	BusID		"PCI:1:0:0"
	Driver "nvidia"
	Option "NvAGP" "3"
	Option "DigitalVibrance" "0"
	Option "TransparentIndex" "0"
	Option "CursorShadowAlpha" "64"
	Option "CursorShadowXOffse" "4"
	Option "CursorShadowYOffset" "2"
	Option "NoLogo" "TRUE"
	Option "Twinview" "TRUE"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" "31-80"
	Option "SecondMonitorVertRefresh" "56-85"
	Option "MetaModes" "1280x1024,1280x1024"
	Option "ConnectedMonitor" "DFP , DFP"
EndSection

Section "Monitor"
	Identifier	"S/M 770TFT"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"S/M 770TFT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by erlyrisa on 2006-03-31
-umm I don't have a dual output G.card.- but thanks anyway - I was hoping to try and doit the traditional way with two gICs. - interesting info though - and should serve handy when I get some better uptodate hardware.

---

### Post by erlyrisa on 2006-03-31
actually - I found that there is a really easy way to spread the desktop over all the monitors.

-- if any on is interested than all you have to do is add this line to your serverlayout section in Xorg/Xfree .conf

Option "Xinerama" "True"

Walla - your desktop is now the Mirosoft way -
I haven't decided if this is the better way or not just yet.

---

