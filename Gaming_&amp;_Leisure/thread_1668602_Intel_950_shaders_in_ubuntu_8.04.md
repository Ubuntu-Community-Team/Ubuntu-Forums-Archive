---
title: "Intel 950 shaders in ubuntu 8.04"
date: 2011-01-16
forum: Gaming &amp; Leisure
---

### Post by Ethereal_Intellect on 2011-01-16
Hey there. I've searched around for solutions but found nothing, so I decided to post here. If it's the wrong section please move it.

I have an EEEpc 900HA netbook with ubuntu 8.04 (Hardy) installed. I know I should update it, but it has a lot of data on it currently which would make it kind of a hassle.

Anyway I've installed Braid and Super Meat Boy recently, both reported to work, especially meat boy, but I got the same error, the graphics card shaders aren't recognized by either game, and they wont start.

Any help is appreciated. Here is my xorg.conf.
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "xtrap"
	Load  "glx"
	Load  "dbe"
	Load  "GLcore"
	Load  "dri"
	Load  "extmod"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  200   110	# mm
	Identifier   "Monitor0"
	VendorName   "HSD"
	ModelName    "325"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
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
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

