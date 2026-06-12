---
title: "Xorg configuration"
date: 2005-12-18
forum: Desktop Environments
---

### Post by honeydew on 2005-12-18
I recently installed ubuntu on my gateway solo 5300.  Im trying to configure my xorg file properly.  When I was using freebsd I simply took this configuration from the gentoo wiki([http://64.233.187.104/search?q=cache:lLkhHMAToZEJ:gentoo-wiki.com/Gateway_Solo_5300+gentoo+solo+5300&hl=en&lr=&client=firefox&strip=1](http://64.233.187.104/search?q=cache:lLkhHMAToZEJ:gentoo-wiki.com/Gateway_Solo_5300+gentoo+solo+5300&hl=en&lr=&client=firefox&strip=1))

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "PS2Mouse" "CorePointer"
	InputDevice    "USBMouse" "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/lib/X11/rgb"
	ModulePath   "/usr/lib/modules"
    FontPath 	"/usr/share/fonts/misc"
    FontPath 	"/usr/share/fonts/TTF"
    FontPath 	"/usr/share/fonts/Type1"
    FontPath 	"/usr/share/fonts/75dpi"
    FontPath 	"/usr/share/fonts/100dpi"
    FontPath 	"/usr/local/share/fonts"
    FontPath 	"/usr/share/fonts"
    FontPath 	"/usr/X11R6/lib/X11/fonts"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "xtrap"
	Load  "glx"
	Load  "type1"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
   Identifier  "PS2Mouse"
   Driver      "mouse"
   Option      "Protocol"              "PS/2"
   Option      "Device"                "/dev/mouse"
   Option      "Emulate3Buttons"       "true"
   Option      "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
   Identifier  "USBMouse"
   Driver      "mouse"
   Option      "Protocol"              "ExplorerPS/2"
   Option      "Device"                "/dev/usbmouse"
   Option      "Emulate3Buttons"       "false"
   Option      "ZAxisMapping"          "4 5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-48.5
	VertRefresh  55-90
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "HWCursor"           	# [<bool>]
        #Option     "SWCursor"           	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "UseBIOS"            	# [<bool>]
        #Option     "LCDClock"           	# <freq>
        #Option     "ShadowStatus"       	# [<bool>]
        #Option     "CrtOnly"            	# [<bool>]
        #Option     "TvOn"               	# [<bool>]
        #Option     "PAL"                	# [<bool>]
        #Option     "ForceInit"          	# [<bool>]
        #Option     "Overlay"            	# [<str>]
        #Option     "TransparencyKey"    	# [<str>]
	Identifier  "Card0"
	Driver      "savage"
	VendorName  "S3 Inc."
	BoardName   "86C270-294 Savage/IX-MV"
	BusID       "PCI:1:1:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes     "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1024x768"
	EndSubSection
EndSection

```

this would not work.. X.org would not even start.. so I just took some of the settings from this file and placed them in mine

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
	Identifier	"Card0"
	Driver		"savage"
	BusID		"PCI:1:1:0"
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-48.5
	VertRefresh  55-90
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes     "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1024x768"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

this allowed xorg to boot up.. however I still not achieve a 1024x768 resolution.. I looked in the gnome settings and my max setting is 800x600.. I have been playing with it for some time.. if anyone has any insight, please Im all ears.

---

### Post by Redindian on 2005-12-18
Under section 'screen", subsection 'display' you have only one type of resolution.... sudo dpkg-reconfigure xserver-xorg (backup your xorg.xconf file), try to include 832x643, 800x600 and check whether you have all the options in system-preference-screen resolution. 

Check this link also [http://ubuntuforums.org/showpost.php...9&postcount=21](http://ubuntuforums.org/showpost.php...9&postcount=21) for screen resolution problems

---

### Post by honeydew on 2005-12-18
I looked in my log files and found this rubish.. harumph.. Ive gotten this resolution in freebsd before.. tis quite disconcerning.


(II) SAVAGE(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) SAVAGE(0): Not using mode "1024x768" (no mode of this name)
(--) SAVAGE(0): Found 13 modes at this depth:
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 43Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 43Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 48Hz, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [178] 720 x 576, 75Hz
(--) SAVAGE(0): Virtual size is 800x600 (pitch 800)

---

### Post by afhp on 2005-12-18
It does look like your xorg.conf file has some missing "Modes" lines (although you have the bare minimum to make it work). X tends to fall back to "the best it can" when it cannot do what you ask ; when that happens, more often than not I've found it to be a problem with what X *thinks* the screen is capable of. That is, the "Monitor" section and particularly the refresh rates (HorizSync and VertRefresh). Where did you get these values from ?

---

### Post by craty on 2005-12-19
if you are sure that you have given proper values of HorzSync and VertRefresh (make sure from your manual or from website) and still you are not getting the 1024x768 resolution then try this:
Just change shared video memory in BIOS from 1024K (1MB) to 8192K (8MB)and you will not have any problems after that!!!

you can refer to my thread [http://ubuntuforums.org/showthread.php?t=104064&page=2](http://ubuntuforums.org/showthread.php?t=104064&page=2)

if still its not working then post your /etc/X11/xorg.conf & /var/log/Xorg.0.log files(or give any links for those files.)

Best of luck

---

