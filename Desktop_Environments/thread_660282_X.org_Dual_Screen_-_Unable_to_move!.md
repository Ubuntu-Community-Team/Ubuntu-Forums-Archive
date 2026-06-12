---
title: "X.org Dual Screen - Unable to move!"
date: 2008-01-06
forum: Desktop Environments
---

### Post by mikesena on 2008-01-06
Hi,

I am trying to fix an issue with dual screens on my laptop.
I cannot move windows for some reason!  I have two configurations for X, one that is single screen + 3D acceleration, and the other twin view.  3D does allow me to move windows, but for some reason my twin setting doesn't.

Can anyone please see why / make suggestions to my config anyway?

Thanks
Michael

**Twin View Config**
```
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
#    Load        "type1"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    #Load       "glx"
# This loads the DRI module
    #Load       "dri"

EndSection

Section "Files"
    FontPath   "/usr/share/fonts/misc"
    FontPath   "/usr/share/fonts/100dpi:unscaled"
#   FontPath   "/usr/share/fonts/75dpi:unscaled"
    FontPath   "/usr/share/fonts/TTF"
    FontPath   "/usr/share/fonts/Type1"
#   FontPath   "/usr/lib/X11/fonts/local/"
#   FontPath   "/usr/lib/X11/fonts/misc/"
#   FontPath   "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/lib/X11/fonts/100dpi/:unscaled"
#   FontPath   "/usr/lib/X11/fonts/Speedo/"
#   FontPath   "/usr/lib/X11/fonts/Type1/"
#   FontPath   "/usr/lib/X11/fonts/TrueType/"
#   FontPath   "/usr/lib/X11/fonts/freefont/"
#   FontPath   "/usr/lib/X11/fonts/75dpi/"
    FontPath   "/usr/lib/X11/fonts/100dpi/"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "InputDevice"
    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us,dvorak"
    Option "XkbVariant"	""
EndSection

Section "InputDevice"
    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "Auto"	# Auto detect
    Option "Device"      "/dev/input/mice"
    Option "ZAxisMapping"   "4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

###############
## MONITOR 1 ##
###############
Section "Monitor"
    Identifier  "Laptop Monitor"
    HorizSync   31.5 - 48.5
    VertRefresh 56.0-65.0
    modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma 1.0
EndSection

##############
## DEVICE 1 ##
##############
Section "Device"
    Identifier  "Laptop Device"
    Driver      "i810"
    VideoRam    65536
    Busid		"PCI:0:2:0"
    Screen	0
    Option		"MonitorLayout"	"CRT,LFP"
EndSection

##############
## SCREEN 1 ##
##############
Section "Screen"
    Identifier  "Laptop Screen"
    Device      "Laptop Device"
    Monitor     "Laptop Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth	24
        Virtual	1024	768
        Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
    EndSubSection
EndSection

###############
## MONITOR 2 ##
###############
Section "Monitor"
	Identifier	"Second Monitor"
	Horizsync	31.5-57.0
	Vertrefresh	50.0-90.0
	modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
	modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
	modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
	modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
	modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
	modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
	Gamma	1.0
EndSection

##############
## DEVICE 2 ##
##############
Section "Device"
    Identifier  "Second Device"
    Driver      "i810"
    VideoRam    65536
    Busid	"PCI:0:2:0"
    Screen	1
    Option		"MonitorLayout"	"CRT,LFP"
EndSection

##############
## SCREEN 2 ##
##############
Section "Screen"   
	Identifier	"Second Screen"
	Device		"Second Device"	
	Defaultdepth	24
	Monitor		"Second Monitor"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"1024x768@43"	"1024x768@70"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Second Screen" 0 1
	screen 1 "Laptop Screen" rightof "Second Screen"
	Inputdevice	"Keyboard1"
	Inputdevice	"Mouse1"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
   Mode 0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection
```
**3D**
```
# File generated by xorgconfig.

#
# Copyright 2004 The X.Org Foundation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# The X.Org Foundation BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of The X.Org Foundation shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from
# The X.Org Foundation.
#

# **********************************************************************
# Refer to the xorg.conf(5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
#    Load        "type1"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    Load       "glx"
# This loads the DRI module
    Load       "dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

#    RgbPath	"/usr/share/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# 

    FontPath   "/usr/share/fonts/misc"
    FontPath   "/usr/share/fonts/100dpi:unscaled"
    FontPath   "/usr/share/fonts/75dpi:unscaled"
    FontPath   "/usr/share/fonts/TTF"
    FontPath   "/usr/share/fonts/Type1"
#    FontPath   "/usr/lib/X11/fonts/local/"
#    FontPath   "/usr/lib/X11/fonts/misc/"
#    FontPath   "/usr/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/lib/X11/fonts/Type1/"
#    FontPath   "/usr/lib/X11/fonts/TrueType/"
#    FontPath   "/usr/lib/X11/fonts/freefont/"
#    FontPath   "/usr/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Ctrl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Uncomment this to disable the <Ctrl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Ctrl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option	"Xleds"      "1 2 3"

#    Option "LeftAlt"     "Meta"
#    Option "RightAlt"    "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"    "pc105"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"    "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"   "de"
# or:
#    Option "XkbLayout"   "de"
#    Option "XkbVariant"  "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions"  "ctrl:swapcaps"

# These are the default XKB settings for Xorg
#    Option "XkbRules"    "xorg"
#    Option "XkbModel"    "pc105"
#    Option "XkbLayout"   "us"
#    Option "XkbVariant"  ""
#    Option "XkbOptions"  ""

#    Option "XkbDisable"

    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "Auto"	# Auto detect
    Option "Device"      "/dev/input/mice"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"	"256"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"	"9600"
#    Option "SampleRate"	"150"

# Mouse wheel mapping.  Default is to map vertical wheel to buttons 4 & 5,
# horizontal wheel to buttons 6 & 7.   Change if your mouse has more than
# 3 buttons and you need to map the wheel to different button ids to avoid
# conflicts.

    Option "ZAxisMapping"   "4 5 6 7"

# Emulate3Buttons is an option for 2-button mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the xorg.conf man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "1412"
#    Option     "MaxX"          "15184"
#    Option     "MinY"          "15372"
#    Option     "MaxY"          "1230"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "231"
#    Option     "MaxX"          "3868"
#    Option     "MinY"          "3858"
#    Option     "MaxY"          "272"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonThreshold"       "17"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "My Monitor"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   31.5 - 48.5

#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 50-100

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset	"generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver     "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# intalled.

#    BusID      "PCI:0:10:0"

#    VideoRam	256

#    Clocks	25.2 28.3

EndSection

# Device configured by xorgconfig:

Section "Device"
    Identifier  "** Intel i810 (generic)               [i810]"
    Driver      "i810"
    #VideoRam    65536
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "** Intel i810 (generic)               [i810]"
    Monitor     "My Monitor"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
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

### Post by public_void on 2008-01-06
You need to add Xinerama support. First install Xinerama
```
sudo apt-get install xinerama
```Then add the follow option to your ServerLayout
```
[FONT=Verdana]Option "Xinerama" "true"[/FONT]
```Hopefully that such fix it. If not this [thread]("http://ubuntuforums.org/showthread.php?t=221174") is a howto for different methods for setting up dual monitors. The xinerama methods is detail there also.

---

