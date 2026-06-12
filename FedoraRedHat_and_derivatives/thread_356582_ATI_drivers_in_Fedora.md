---
title: "ATI drivers in Fedora"
date: 2007-02-08
forum: Fedora/RedHat and derivatives
---

### Post by igknighted on 2007-02-08
OK, I realize this isn't the right site, but I thought it might be worth a stab.  I am testing Fedora 6, and absolutely love it.  I've never been much of a gnome fan, but Fedora is onto something.  I am just having issues with the ATI drivers so I can play my games through Cedega (which is already installed and ready to go).  I downloaded the drivers from the ATI site (the 3rd party repo ones were no good) and built them into RPMs.  These I then installed, edited my xorg.conf properly (I believe) and now I get nothing but mesa inderect, no direct rendering.  This is the newest 8.33.6 ATI build.  This is my xorg.conf:
```

# Xorg configuration created by pyxf86config

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen 1" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
#   Load	"type1"
#   Load	"freetype"
    Load	"extmod"
#   Load	"synaptics"
    Load	"vbe"
    Load        "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 56 - 75
    HorizSync	30 - 79
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "fglrx" # do not remove vesa
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier	"Screen 1"
    Device	"VESA"
    Monitor	"Generic Monitor"
    #Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth		8
        ViewPort	0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        Modes		"1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection


EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection

```

---

