---
title: "dual monitor, different monitors, different resolutions"
date: 2006-06-20
forum: Desktop Environments
---

### Post by degel3030 on 2006-06-20
ok so i installed nvidia drivers and afterwards i have been trying to get dual monitor support, i would like it to span across the 2 monitors
i have a 6600 nvidia card with dvi and vga out, the monitor that seems to be the 'main' or 'default' or whatever is the vga, when i restart X the login screen the 2 monitors are working, but when i log into gnome the one on dvi goes out
thanks for any help or suggestions im hoping to get this going soon



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
#	Load	"dri"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
Option "NoLogo" "1"
Option "RenderAccel" "0"
Option "CursorShadow" "1"
Option "Coolbits" "1"
Option "ConnectedMonitor" "crt, dfp"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x1024,1680x1050; 1024x768,NULL"
Option "SecondMonitorHorizSync" "31-83"
Option "SecondMonitorVertRefresh" "56-75"
# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"CM715"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"CM715"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen	0	"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by IYY on 2006-06-20
The code looks right to me. In the "Device" section, you might want to add:

```

Option "TwinViewOrientation" "RightOf"
```

Though I don't think this is the problem.

---

### Post by chavo on 2006-06-20
I have a similar setup one 1280x1024 and one 1400x900, the only difference I see is in the metamodes line I have only one. I remember having the same problem in KDE everytime I logged in. I could run xrandr and fix it but then I tried taking out the extra metamodes. I'm not sure if you need the extra one or not, but just try to remove it ans see what happens.

---

### Post by degel3030 on 2006-06-20
did you mean take out all of these 
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"


well i did that, and then i really messed things up, im pretty much stuck right now


my video card is a 6600 on pciE slot, the vga out is going to a hitachi cm715 and the dvi out is going to a dell 2005fpw, im kind of stuck as i have looked and looked for resources to find any info i can, almost all are for dual monitors of the same type (which i wish i had now)
well if there is any more help that would be great

---

### Post by SonicChao on 2006-06-20
They didn't mean to delete all of that and replace it with

> Option "TwinViewOrientation" "RightOf"

They ment to just add it...

Put everything back you deleted before.

---

### Post by degel3030 on 2006-06-20
well that didnt work, still the same thing, screen is up during the login, but after i get into gnome its a blank screen (with no signal going to it, the lights turn orange when that happens, green when there is a signal)

---

