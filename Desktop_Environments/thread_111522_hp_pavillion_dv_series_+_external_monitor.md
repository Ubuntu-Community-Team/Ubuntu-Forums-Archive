---
title: "hp pavillion dv series + external monitor"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Gandalf on 2006-01-02
Hello

I have an HP Pavilion dv1071ea with a widescreen LCD that runs on 1280x768 resolution, the vard is an intel Intel Corporation 82852/855GM Integrated Graphics Device (driver i810) and i have a problem using an external crt 17" monitor :( actually when i plug the monitor and press fn + F4 untill i see both screens i have to manually switch to 1024x768 (which i don't mind at all) but since it's a widescreen, linux will stretch it to cover the whole screen (unlinke windows unfortunately, windows is out of ma life so no way to use it, i jusr have it to test things!!) anyway i took some pics of wat i'm talking about, sorry for the low resolution

A pic of the LCD on linux where you can see the screen is stretched
[[IMG]http://img408.imageshack.us/img408/1166/lcdlinux10248dg.th.jpg[/IMG]](http://img408.imageshack.us/my.php?image=lcdlinux10248dg.jpg)

but on windows the LCD will have black area at right & left of the screen so it will not be stretched
[[IMG]http://img408.imageshack.us/img408/3151/lcdwin10240qn.th.jpg[/IMG]](http://img408.imageshack.us/my.php?image=lcdwin10240qn.jpg)

unfortunately this will affect on how the screen is viewd on the CRT monitor, look at the below image, on linux only a part of the screen is shown :(
Linux -> [[IMG]http://img408.imageshack.us/img408/8673/crtlinux10244kk.th.jpg[/IMG]](http://img408.imageshack.us/my.php?image=crtlinux10244kk.jpg)
windows -> [[IMG]http://img408.imageshack.us/img408/3640/crtwin10243df.th.jpg[/IMG]](http://img408.imageshack.us/my.php?image=crtwin10243df.jpg)

I noticed one thing, if i turn off the LCD (only output to CRT) the resolution will be correct but yet if i do this i cannot see any video file, it will just put blue screen instead of the video don't know why!
[[IMG]http://img410.imageshack.us/img410/9241/crtlinux1024lcdoff7yy.th.jpg[/IMG]](http://img410.imageshack.us/my.php?image=crtlinux1024lcdoff7yy.jpg)

here's a copy of my xorg.conf file
```

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
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
	Option	"XaaNoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
  HorizSync   31.5 - 48.5
  VertRefresh 50-70
  ModeLine "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768"
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

```

If someone can help i really appreciate it!

Thx in advance

---

### Post by Gandalf on 2006-01-02
After a little search, i ended up trying it on my suse installation and it actually works there, so i tried to make xorg.conf look like suse one (device and monitor parts) and it actually worked, the screen is stretched on the laptop but it will not be displayed as a part of the screen to the crt, but i still have problems
[LIST=1]
[*]Video files are not displayed -> only blue screen
[*]I have to change laptop rsolution to 1024x768 in order to use it, cannot output diff res to the crt screen
[*]the mouse pointer when it is animated it flickers a lot :S
[/LIST]

here's a copy of the new xorg.conf file
```

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

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"fr"

	Option		"XkbVariant"	"latin9"

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

  Option       "NoDDC"

  Option       "Clone" "yes"

  Option       "CloneRefresh" "50-60"

  Option       "SaXDualVSync" "50-60"

  Option       "SaXDualHSync" "off"

  Option       "MonitorLayout" "CRT,LFP"

  Option       "SaXDualHead" ""

  Option       "SaXDualMode" "off"

#  Option       "SaXDualMonitorModel" "1024X768HZ"

#  Option       "SaXDualMonitorVendor" "--> VESA"

  Option       "SaXDualOrientation" "off"

  Option       "SaXDualResolution" "off"

  VendorName   "Intel"

EndSection



Section "Monitor"

	Identifier	"Generic Monitor"

  DisplaySize  302 188

	Option		"DPMS"

  HorizSync   31.5 - 48.5

  VertRefresh 50-70

  UseModes     "Modes[0]"

EndSection



Section "Modes"

  Identifier   "Modes[0]"

  ModeLine "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795

  Modeline 	"1024x600" 53.78 1024 1072 1176 1328 600 601 604 623

  Modeline 	"1024x600" 52.95 1024 1072 1176 1328 600 601 604 623

  Modeline 	"1024x600" 51.49 1024 1064 1168 1312 600 601 604 623

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"

	Monitor		"Generic Monitor"

	DefaultDepth	24

	SubSection "Display"

		Depth		1

		Modes		"1280x768" "1024x768"

	EndSubSection

	SubSection "Display"

		Depth		4

		Modes		"1280x768" "1024x768"

	EndSubSection

	SubSection "Display"

		Depth		8

		Modes		"1280x768" "1024x768"

	EndSubSection

	SubSection "Display"

		Depth		15

		Modes		"1280x768" "1024x768"

	EndSubSection

	SubSection "Display"

		Depth		16

		Modes		"1280x768" "1024x768"

	EndSubSection

	SubSection "Display"

		Depth		24

		Modes		"1280x768" "1024x768"

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



```

---

### Post by simohell on 2006-01-03
There are quite a few threads for intel 855 chipset and WXGA. You can try seaches like "i810 1280x768" and "i810 1280x800". You will probably need a tool called 855resolution (or 915resolution as I understood it works also for 855).

Also checking "man i810" - the manual pages for Xorg driver i810 - can give you some clue what parameters to try.

---

