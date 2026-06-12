---
title: "1400x1050 on Notebook (915GM) and external TFT (works but not fine)"
date: 2006-10-14
forum: Desktop Environments
---

### Post by 8200 on 2006-10-14
Hi. I have got a HP NX6110 notebook with intel 915gm videocard and a screen resolution of 1400x1050. Yesterday I bought a LG L200CE TFT with also 1400x1050 resolution. So if I am home I want to use the LG screen.

I have tried very much variations :evil: of xorg.confs but only this one works. With this config my notebook-screen is the main screen and the LG is right beside. When I am moving the mouse at the edge of the LG it scrolls up - so it seems that there is an higher resolution than it should be (but the LG is connected with 1400x1050).

This thread helped me solving the issue with the resolution and the sycnhroning frequency:
[http://ubuntuforums.org/showthread.php?t=203905](http://ubuntuforums.org/showthread.php?t=203905)
I am starting 915resolution with this values:
915resolution 3c 1400 1050 8 1864 1089
915resolution 4d 1400 1050 16 1864 1089
915resolution 5c 1400 1050 32 1864 1089

Here is my xorg.conf:
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"FlipPrimary" "true"
        Option		"ForceBIOS" "1920x1440=1400x1050"
        Screen		0
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"FlipPrimary" "true"
        Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor extern"
	Option		"DPMS"
	HorizSync	28.0-83.0
	VertRefresh	56.0-75.0
	DisplaySize	408 306
	Modeline	"1400x1050_60.00" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen extern"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Monitor		"Generic Monitor extern"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	Screen		1 "Default Screen extern" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```



WOuld be really great if you could help - I'm getting sick :mad:  with this problem. It would also be ok :) if I could use only the LG at home (it's no need to use the notebook screen and the external together).


THANK YOU!

---

### Post by 8200 on 2006-10-14
This the perfect desktop:
[IMG]http://forum.geizhals.at/files/2711/desktop_perfekt.JPG[/IMG]
Here you can see what happens when I am moving the mouse into the buttom right korner
[IMG]http://forum.geizhals.at/files/2711/desktop_scrollen.JPG[/IMG]


Why is it possible to scroll into these area by moving the mouse to the right or to the bottom (something must be wrong withe the xorg.conf)?

---

### Post by 8200 on 2006-10-15
Update:
I managed to have the same sceen on the Notebook and the LG, but I would like to have them beside. The LG should be the main screen and the Notebook rightof it. Something must be wrong with the xorg.conf. I have tried so in the xorg.conf but only the mousepointer is only on one screen, everything else is the same.

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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"FlipPrimary" "true"
#	Option		"ForceBIOS" "1920x1440=1400x1050"
        Screen		0
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"FlipPrimary" "true"
        Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor extern"
	Option		"DPMS"
	HorizSync	28.0-83.0
	VertRefresh	56.0-75.0
	DisplaySize	408 306
	Modeline	"1400x1050_60.00" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		1400 1050
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen extern"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Monitor		"Generic Monitor extern"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		1400 1050
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 1	"Default Screen extern" 1 1
	Screen 0	"Default Screen" RightOf "Default Screen extern"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by 8200 on 2006-10-15
Here is the right code for cloned option:

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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
        Option		"Clone"	"true"
#	Option		"FlipPrimary" "true"
	Option		"VBERestore" "yes"
	Screen 1
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"Clone"	"true"
	Option		"VBERestore" "no"
	Option		"DevicePresence" "yes"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor extern"
	Option		"DPMS"
	HorizSync	28.0-83.0
	VertRefresh	56.0-75.0
	DisplaySize	408 306
	Modeline	"1400x1050_60.00" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		1400 1050
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen extern"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller extern"
	Monitor		"Generic Monitor extern"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		1400 1050
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen extern"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "false"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

