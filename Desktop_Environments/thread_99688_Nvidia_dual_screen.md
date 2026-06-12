---
title: "Nvidia dual screen"
date: 2005-12-06
forum: Desktop Environments
---

### Post by ebmar on 2005-12-06
Hello.

I'm trying to get my 2 screens to work properly with 1280x1024 resolution.

This is how my xorg.conf file looks like;

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "randr"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
#       Load    "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option  "hwcursor" "off"
        Screen 0
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option  "hwcursor" "off"
        Screen 1
EndSection

Section "Monitor"
        Option  "CalcAlgorithm" "CheckDesktopGeometry"
        DisplaySize     360 270
        Identifier      "Monitor[0]"
        Option          "DPMS"
        HorizSync       31-93
        VertRefresh     50-75
        UseModes        "Modes[0]"
EndSection

Section "Monitor"
        Option  "CalcAlgorithm" "CheckDesktopGeometry"
        Identifier      "Monitor[1]"
        Option          "DPMS"
        HorizSync       28-87
        VertRefresh     50-70
        UseModes        "Modes[1]"
EndSection

Section "Modes"
 Identifier     "Modes[0]"
 Modeline       "1600x1200" 202.50 1600 1664 1856 2160 1200 1201 1204 1250
EndSection

Section "Modes"
 Identifier     "Modes[1]"
 Modeline       "1600x1200" 189.00 1600 1664 1856 2160 1200 1201 1204 1250
EndSection


Section "Screen"
        Identifier      "Screen[0]"
        Device          "Device[0]"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1024x768"
        EndSubSection
EndSection
Section "Screen"
       Identifier      "Screen[1]"
        Device          "Device[1]"
        Monitor         "Monitor[1]"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  Option       "Clone" "off"
  Option       "Xinerama" "on"
        Screen          "Screen[1]"
        Screen       "Screen[0]" RightOf "Screen[1]"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0660
EndSection

```

My resolution becomes 800x600, and I dont know why..
I cant change the resolution with the randr thing, I get this error: 

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

Does anyone have a solution?

---

### Post by Joe_CoT on 2005-12-06
the only resolutions i'm seeing you declare are 1600x1200 and 1024x768. did you try putting 1280x1024 first? Are you sure those are the correct refresh rates for your monitor?

---

### Post by kenichi on 2005-12-11
Hi,

this is my xorg.conf with dual screen setup via nvidia drivers and not xinerama and it works perfect :D

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"
	Option "Xinerama" "false"
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
  Identifier  "Simple Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
  Screen      0 "screen0" 0 0
EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

Section "Monitor"
	Identifier	"monitor0"
	VendorName  "Iiyama"
	ModelName   "AS4612UT"
	HorizSync   24.0-80.0
  VertRefresh 56-85
	Option		  "DPMS" "true"
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
	Identifier	"screen0"
	Device		"nvidia0"
	Monitor		"monitor0"
	DefaultDepth	24
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

# **********************************************************************
# Graphics device section
# **********************************************************************

Section "Device"
	Identifier "nvidia0"
	Driver     "nvidia"
	VendorName "nVidia Corporation"
	BoardName  "NV25 [GeForce4 Ti 4200]"
	BusID      "PCI:3:0:0"
	VideoRam   65536
	Screen     0
	Option     "TwinView" "on"
	Option     "MetaModes" "1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600"
	Option     "TwinViewOrientation" "LeftOf"
	Option     "SecondMonitorHorizSync" "24.0-80.0"
	Option     "SecondMonitorVertRefresh" "56-85"
	Option     "NoLogo" "true"
EndSection

#

Section "DRI"
	Mode	0666
EndSection

```

I hope it helps you...

cheers,
kenichi

---

