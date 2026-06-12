---
title: "Opengl not working on new XPS 210..."
date: 2007-11-30
forum: Dell  Ubuntu Support
---

### Post by Oblique63 on 2007-11-30
Hi, I just did a fresh install of Ubuntu 7.10 gutsy gibbon, and Im having problems getting compiz to work...

my video card is an intel 82G965.
I googled several times looking for anything, but there's not much info on my card that I could find, and the solutions I found to other intel cards (extensive xorg.conf editing, reinstalling mesa, installing 915resolution, etc)  didnt work.

now, Im well aware that some intel cards just arent supported for 3d effects, so just to make sure I ran a few live cds of other distros with compiz 'out-of-the-box', and surprisingly enough when I tried Sabayon, it all worked flawlessly, so I know its possible... what Im not sure about is what libraries and packages I need to make this work with my ubuntu install?...

I did notice that the sabayon cd was using a previous version of mesa (6.5.2 to be exact) Im not sure if this has anything to do with it (I currently have mesa 7.0.1), but if it does, how do I downgrade to that version?  I have the source package for it that I copied off of sabayon's distfiles directory after an emerge -f mesa mesa-progs, but Im not sure how to compile it, there seem some other steps Im missing before doing 'make install' or something...

but anyway, anybody have any Idea how to fix this?

P.S.  Here's my xorg.conf from my ubuntu install and from the sabayon cd if its of any importance...

Ubuntu -
```

Section "Files"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option  "UseFBDev"      "true"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

Section "Monitor"
	Identifier	"DELL E207WFP"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"DELL E207WFP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1680x1050" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
   Option        "Composite" "Enable"
EndSection

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

```


Sabayon -
```

Section "Files"


    #FontPath	"/usr/share/fonts/local/"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath 	"/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
    Load	"type1"
    Load	"freetype"
    Load	"extmod"
    Load	"synaptics"
    Load	"vbe"
   Load        "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option 	"AllowMouseOpenFail" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier		"Synaptics1"
    Driver		"synaptics"
    Option		"SendCoreEvents"	"true"
    Option		"Device"		"/dev/psaux"
    Option		"Protocol"		"auto-dev"
    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS/MacBook TouchPads
    #Option		"MaxSpeed"		"0.7"
    #Option		"MinSpeed"		"0.18"
    #Option		"AccelFactor"		"0.08"
    #Option		"TopEdge"		"120"
    #Option		"LeftEdge"		"120"
    #Option		"BottomEdge"		"830"
    #Option		"RightEdge"		"650"
    #Option		"FingerLow"		"25"
    #Option		"FingerHigh"		"30"
    # MacBook touchpad
    #Option		"MaxTapTime"		"180"
    #Option		"MaxTapMove"		"220"
    #Option		"MaxDoubleTapTime"	"180"
    #Option		"VertScrollDelta"	"20"
    #Option		"HorizScrollDelta"	"50" 
    #Option		"TapButton2"		"3"
    #Option		"TapButton3"		"2"
    #Option		"VertTwoFingerScroll"	"1"

    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    
    Option	"AutoRepeat"	"500 5"
    Option      "XkbModel"      "pc105"
    Option	"XkbLayout"	"us"
    Option      "XkbRules"      "xorg"
    # Macintosh keyboard
    #Option	"XkbOptions"	"lv3:rwin_switch"

EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom1"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom2"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom3"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"

    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"ImPS/2"
    Option	"ZAxisMapping"	"4 5"
     
EndSection

Section "InputDevice"
    Identifier	"Mouse2"
    Driver	"mouse"
    Option	"Protocol"	"ImPS/2"
    Option	"Device"	"/dev/input/mice"
    Option 	"ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 43 - 60
    HorizSync	28 - 80
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "i810" # do not remove vesa
    #Option "RenderAccel" "on"
    Option "XAANoOffscreenPixmaps"
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
    Option "AddARGBGLXVisuals" "true"

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
    InputDevice	"Mouse1" "CorePointer"
    InputDevice	"Mouse2" "SendCoreEvents"
    #InputDevice "Synaptics1" "SendCoreEvents"
    #InputDevice "wacom1" "SendCoreEvents"
    #InputDevice "wacom2" "SendCoreEvents"
    #InputDevice "wacom3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   Option "Composite" "Enable"
EndSection

```

---

### Post by sciurus on 2007-12-02
The problem is not with your X configuration.[ Ubuntu doesn't make this very clear]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226"), but COmpiz on this video chipset is disabled for a reason- it breaks video playback using XV. However, XV is by no means a requirement for playing videos. Here are two steps for enabling compiz:

   1. run gstreamer-properties and change the video output to 'no xv'
   2. run the following command mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

Now you can start desktop effects from the appearance capplet. If you do have problems, just disable compiz. Don't expect any support.

---

