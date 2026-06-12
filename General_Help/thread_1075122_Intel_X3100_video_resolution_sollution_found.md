---
title: "Intel X3100 video resolution sollution found"
date: 2009-02-19
forum: General Help
---

### Post by dooco on 2009-02-19
I have a dell inspiron 530s.  and like many of you have had the issue with my intel x3100 integrated graphics card of being locked into a crummy resolution.  Ubuntu is the only one i had this problem with.  o here is how i fixed it.  I powered up sabayon linux 4.0 to a live cd environment and opened my xorg.config file and copied all the contents to my ubuntu xorg.config file and POOF i now have all my video options and resolutions that i had on sabayon.  but in ubuntu.  give it a try i am also posting my sabayon xorg file so everyone dosn't have to go dl it.  It worked for me i hope it helps some people in the community.

> Section "Module"
    SubSection  "extmod"
       Option    "omit xfree86-dga"
    EndSubSection
    Load	"i2c"
    Load	"ddc"
    Load	"vbe"
   Load        "dri"
EndSection


Section "ServerFlags"
     Option 	"AllowMouseOpenFail" "true"
EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier	"Generic Monitor"
    VertRefresh 43 - 60
    HorizSync	28 - 80
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver    "intel"
    #Option "RenderAccel" "on"
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
    Option "UseEvents" "True"
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
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier	"Main Layout"
    Screen 0 	"Screen 1"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection


---

