---
title: "Slow video performance"
date: 2006-03-12
forum: Desktop Environments
---

### Post by ubuntu_jazzbach on 2006-03-12
I have breezy installed on a hp pavillion dv1000 laptop with 1280 mb of ram and an intel 82852/855 integrated graphics device and everything works FLAWLESLY !!!... except taht I have a very, VERY slow video layout. For example, whenever I have 3 firefox windows and I change between them, the transition becomes soooooooooooooo sloooooooooooooooooooow. Does it have to do with the video ram ???  HEEEELP !!!!

---

### Post by taurus on 2006-03-12
What video driver you are currently using for your laptop?  Try using "i815" to see if it improves the refreshing rate for your windows then.  Don't forget to restart X (<Ctrl><Alt>Backspace) to the new setting will be in effect!
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by ubuntu_jazzbach on 2006-03-12
This is the info I got after running the lspci command
_____
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
_____

---

### Post by taurus on 2006-03-12
What video driver do you currently use in /etc/X11/xorg.conf?  Try replacing it with "i815" then...

---

### Post by ubuntu_jazzbach on 2006-03-12
This is the output of my /etc/X11/xorg.conf file:
________________
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
_______________

---

