---
title: "xinerama second display with moire pattern"
date: 2005-09-27
forum: Desktop Environments
---

### Post by digitalmouse on 2005-09-27
loathing a double-post, yet not wanting to hijack Cereal2nd's related thread with a similar yet different problem, i thought i would post this new into the kubuntu-specific sections.

i've done a dual-card, dual-monitor setup on this machine (AMD 1.3Ghz/768MB RAM) using Mandrake many years ago (but unfortunately never saved that configuration), so i know this particular hardware is capable of doing it.  This also worked under Windows98se and WinXP Pro on the same hardware.
 
using HenriQuemaia's excellent [HowTo]("http://www.ubuntuforums.org/showthread.php?t=53050") on Xinerama for ubuntu, i followed all the steps, applied various changes, and even searched through the forums for something similar to my problem, before tossing up my hands in confusion.  maybe i've been looking at this too long and i no-longer see the obvious.

the problem is thus:  using the above HowTo as my base, I now have an extended desktop spanning two monitors, but only see the desktop on the primary (leftmost) screen.  the right screen shows only the default X-server grey moire pattern- this tells me that at least it is starting up.  

the desktop switcher in the taskbar shows the wider configuration, and I can move the mouse and application windows into that right-hand space, abeit blindly.  mouse does disappear when moving it into that righthand screen (it is not stopped at right edge of the primary screen).

using kubuntu 5.04 with KDE 3.4.0 and kernel 2.6.10-5-386.  

here is the current xorg.conf file:
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Identifier	"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"s3"
	Driver		"vesa"
	BusID		"PCI:0:11:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"highscreen"
	HorizSync	30-69
	VertRefresh	47-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"primary"
	Device		"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"secondary"
	Device		"s3"
	Monitor		"highscreen"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"primary"
	Screen	1	"secondary" RightOf "primary"
	Option		"Xinerama" "true"
	Option		"Clone" "off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

i noticed in other xinerama posts in this forum that the 
	Option		"Xinerama" "true"
appears in another section of the config file, like so:
```
Section "ServerFlags"
  Option "Xinerama" "true"
EndSection
```
does anyone know where this Xinerama option should *really* go?  

tips and suggestions welcome!

thanks!

---

