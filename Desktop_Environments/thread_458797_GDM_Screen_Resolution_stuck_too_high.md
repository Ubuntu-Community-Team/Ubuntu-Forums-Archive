---
title: "GDM Screen Resolution stuck too high"
date: 2007-05-30
forum: Desktop Environments
---

### Post by Flatline-kun on 2007-05-30
I know there are a myriad of posts about this issue, but I have already followed the steps in them to no avail. My GDM screen has always defaulted to 1600x1200 after the initial Ubuntu install, but removing the mode from my xorg.conf always fixed the problem. I installed Feisty and had the same problem - and fixed it by removing the modes as I had before. It worked fine, GDM was at 1280x1024.
     Then I updated the kernel from 2.6.20-15-generic to 2.6.20-16-generic and now even with the 1600x1200 resolution removed GDM is back to 1600x1200! I don't know how updating the kernel can possibly effect this, but it is the only thing I've changed! I am perplexed how my screen is at a resolution that is not in my xorg.conf!
     As I said, I have read through all the posts I could find, and have checked and done what thay all say and am at the end of my rope here! I am including my xorg.conf for your perusal. If you have any suggestions I am open to them.

Thanks, 
Flatlne

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#

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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SAMTRON"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"SAMTRON"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by marcozs on 2007-05-30
I had the same problem... GDM probably picks always the highest resolution you write in xorg.conf... but picking a resolution which is NOT in xorg.conf is really new to me too...

---

