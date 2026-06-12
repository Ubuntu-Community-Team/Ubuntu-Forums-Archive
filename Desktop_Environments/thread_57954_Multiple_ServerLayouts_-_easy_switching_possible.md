---
title: "Multiple ServerLayouts - easy switching possible?"
date: 2005-08-18
forum: Desktop Environments
---

### Post by KillerBOB on 2005-08-18
Hi! First I'd like to point out that I am fairly new to Linux and Ubuntu, and I am still learning new stuff all the time  ;-) . I really like Ubuntu and I have been lurking the forum for quite some time, and that has given me invaluable help in setting my system up. Thank you all!

Ok, so now to the issue:

I have successfully edited my xorg.conf (I used a template I found, with nice comments in the file) to give me TwinView (on a Nvidia 6600GT AGP) on my two CRT-monitors. The thing is I don't really know how to use the other ServerLayout's. I understad that the "TwinView" ServerLayout becomes the default since it's the first one defined i xorg.conf, but what if I would like to use "TwinViewTV" instead?

I have tried this (as the author of the template suggested):
```
startx -- :1 -layout TwinViewTV
```
This indeed starts Twinview on my main monitor and TV. But it only gives the grey background and the "X" mouse-pointer, so I cannot do any work from there.

I would like to be able to choose the ServerLayout to use in some convenient way, if possible? Is it possible without shutting down Gnome? Any suggestions would be happily received  ;-) 

Here is my xorg.conf

```
############################################################
#
# My XF86Config
#
# The goal here is to present a variety of options for your
# XF86Config designed around the proprietary nvidia driver. 
# This config is broken down into "layouts". You don't
# need all the layouts listed here. You only need one. I
# provide multiple layouts because I find it easier to deal
# with them. You can either make your default layout the first
# one in the config, or choose one with the -layout argument:
#
# startx -- -layout OnlyTV
#
# or, to start another X on display :1, do:
#
# startx -- :1 -layout TwinViewTV
#
# where the argument is the layout identifier in the layout
# section.
#
# I group the Device, Screen, and Layout together and name
# them the same. This is to try to illustrate how simple
# all this really is.
#
# !!!!!!!!!!!!!!!!!!!!!!!!!!!
#
# A note regarding Xinerama and Nvidia's "TwinView":
#
# The proprietary Nvidia driver sets up the Xinerama extension
# automatically when you use TwinView. This means that Xinerama
# aware applications, such as mplayer, will be aware of the
# presence of Xinerama. There is NO NEED to add Xinerama manually,
# ordinarily done like this:
#
# Section "ServerFlags"
#   Option "Xinerama" "true"
# EndSection
#
# or:
#
# startx -- +xinerama
#
# IF YOU SEE ANY OF THESE TWO EXAMPLES IN ANY HOWTO OR SAMPLE
# CONFIG, REMOVE THEM! THEY WILL CAUSE TWINVIEW TO NOT WORK
# CORRECTLY!!
#
# !!!!!!!!!!!!!!!!!!!!!!!!!!!
#
# Lastly, this config, even though it works _as is_ _for me_,
# probably will NOT work _as is_ for you. This is intended
# as a guide to help you make YOUR XF86Config. Specifically,
# people's monitors differ, as does support for their AGP
# chipsets. This is where there'll be the most variance.
#
############################################################

############################################################
#
# Common stuff shared by everything in the config
#
############################################################

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
    	Identifier	"Keyboard1"
    	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
    	Identifier	"Mouse1"
    	Driver		"mouse"
    	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

############################################################
#
# The main monitor section. I have this here because this is
# shared by most of the layouts. I also include all the mode-
# lines I use here too. Note that the modelines used by my
# second monitor are here too. All they need to know is the
# name of the modeline in order to use them, where the name
# is "1280x1024_s", in this example. Read my modeline howto
# for more information. (http://www.sh.nu/nvidia/modeline_howto.html)
#
############################################################

Section "Monitor"
    	Identifier  "ViewSonic P810"
	HorizSync   27-86          # You can't just make these values up. You should get them from
    	VertRefresh 50-160           # your monitor's manual (or search google for you monitor's specs)
    	
	# 85 Hz Primary CRT
	Modeline "1024x768_v"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
	Modeline "800x600_v"  56.55  800 840 928 1056  600 601 604 630  -HSync +Vsync

	# 85 Hz Secondary CRT
	Modeline "1024x768_s"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
    	Modeline "800x600_s"  56.55  800 840 928 1056  600 601 604 630  -HSync +Vsync
    	
	# 50 Hz TV
	Modeline "800x600_50.00"  31.15  800 824 904 1008  600 601 604 618  -HSync +Vsync

    	Option	"DPMS"
EndSection

############################################################
#
# The layouts begin here. They are grouped by Device, Screen,
# and Layout. Again, all you need is one of these groups.
#
############################################################

############################################################
#
# Main layout - Twinview on both monitors at 1024x768
#
############################################################

Section "Device"
    Identifier "TwinView"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "DPMS"
    Option "TwinView"
    Option "IgnoreEDID"               "1"
    Option "RenderAccel"              "1"
    Option "CursorShadow"             "1"
    Option "NvAGP"                    "1"
    Option "DigitalVibrance"          "2"
    Option "ConnectedMonitor"         "crt,crt"
    Option "TwinViewOrientation"      "RightOf"
    Option "SecondMonitorHorizSync"   "30-76"
    Option "SecondMonitorVertRefresh" "50-160"
    Option "MetaModes"                "1024x768_v,1024x768_s;1024x768_v,NULL;800x600_v,NULL"
EndSection

Section "Screen"
    Identifier  "TwinView"
    Device      "TwinView"
    Monitor     "ViewSonic P810"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "TwinView"
    Screen	"TwinView"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    Option "blank time"    "10"
    Option "off time"      "20"
EndSection

############################################################
#
# Main TV Layout - Twinview with monitor at 1024x768 and
# TV at 800x600
#
############################################################

Section "Device"
    Identifier "TwinViewTV"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "DPMS"
    Option "TwinView"
    Option "IgnoreEDID"               "1"
    Option "UseEdidFreqs"             "0"
    Option "HWCursor"                 "0"
    Option "NvAGP"                    "2"
    Option "SecondMonitorHorizSync"   "30-50"
    #Option "SecondMonitorHorizSync"   "48.4"
    Option "SecondMonitorVertRefresh" "50"
    Option "TwinViewOrientation"      "RightOf"
    Option "MetaModes"                "1024x768_v,800x600_50.00"
    #Option "TVOutFormat"	      	      "S-VIDEO"
    Option "TVStandard"               "PAL-G"
    Option "ConnectedMonitor"         "crt,TV"
EndSection

Section "Screen"
    Identifier  "TwinViewTV"
    Device      "TwinViewTV"
    Monitor     "ViewSonic P810"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "TwinViewTV"
    Screen	"TwinViewTV"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    Option "blank time"    "10"
    Option "off time"      "20"
EndSection

############################################################
#
# Only the TV, at 800x600. Note the extra Monitor section,
# since we're not using twinview here. This layout will work
# for non-twinview capable cards.
#
############################################################

Section "Monitor"
    Identifier  "TV"
    HorizSync   30-50
    VertRefresh 60
    Option	"DPMS"
EndSection

Section "Device"
    Identifier "OnlyTV"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "DPMS"
    Option "IgnoreEDID"               "1"
    Option "UseEdidFreqs"             "0"
    Option "HWCursor"                 "0"
    Option "NvAGP"                    "2"
    Option "ConnectedMonitor"         "tv"
EndSection

Section "Screen"
    Identifier  "OnlyTV"
    Device      "OnlyTV"
    Monitor     "TV"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "800x600"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "OnlyTV"
    Screen	"OnlyTV"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    Option "blank time"    "10"
    Option "off time"      "20"
EndSection

############################################################
#
# Twinview with TV and Monitor cloned at 640x480
#
############################################################

Section "Device"
    Identifier "TwinViewTV2"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "TwinView"
    Option "DMPS"
    Option "IgnoreEDID"               "1"
    Option "UseEdidFreqs"             "0"
    Option "HWCursor"                 "0"
    Option "NvAGP"                    "2"
    Option "SecondMonitorHorizSync"   "30-50"
    Option "SecondMonitorVertRefresh" "60"
    Option "TwinViewOrientation"      "Clone"
    Option "MetaModes"                "640x480,640x480"
    #Option "TVOutFormat"	      "COMPOSITE"
    Option "TVStandard"               "PAL-B"
    Option "ConnectedMonitor"         "crt,TV"
EndSection

Section "Screen"
    Identifier  "TwinViewTV2"
    Device      "TwinViewTV2"
    Monitor     "ViewSonic P810"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
    EndSubsection
EndSection 

Section "ServerLayout"
    Identifier  "TwinViewTV2"
    Screen	"TwinViewTV2"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

############################################################
#
# Twinview with TV and Monitor cloned at 800x600
#
############################################################

Section "Device"
    Identifier "TwinViewTV3"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "TwinView"
    Option "DMPS"
    Option "IgnoreEDID"               "1"
    Option "UseEdidFreqs"             "0"
    Option "HWCursor"                 "0"
    Option "NvAGP"                    "2"
    Option "SecondMonitorHorizSync"   "30-50"
    Option "SecondMonitorVertRefresh" "60"
    Option "TwinViewOrientation"      "Clone"
    Option "MetaModes"                "800x600,800x600"
    #Option "TVOutFormat"	      "COMPOSITE"
    Option "TVStandard"               "PAL-B"
    Option "ConnectedMonitor"         "crt,TV"
EndSection

Section "Screen"
    Identifier  "TwinViewTV3"
    Device      "TwinViewTV3"
    Monitor     "ViewSonic P810"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
    EndSubsection
EndSection 

Section "ServerLayout"
    Identifier  "TwinViewTV3"
    Screen	"TwinViewTV3"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

############################################################
#
# Separate displays on the same card at 1024x768, using
# modelines and new monitor sections in this group, just
# to keep things clear
#
############################################################

Section "Monitor"
    Identifier  "Dual1"
    HorizSync   27-86
    VertRefresh 50-160
    # 85 Hz
    Modeline "1024x768_v"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
    Option      "DPMS"
EndSection
    
Section "Monitor"
    Identifier  "Dual2"
    HorizSync   30-76
    VertRefresh 50-150
    # 85 Hz
    Modeline "1024x768_s"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
    Option      "DPMS"
EndSection
        
Section "Device"
    Identifier "Dual1"
    Driver "nvidia"
    BusID "PCI:1:0:0"
    Option "NODDC"      "1"
    Screen 0
EndSection
    
Section "Device"
    Identifier "Dual2"
    Driver "nvidia"
    BusID "PCI:1:0:0"
    Option "NODDC"      "1"
    Screen 1
EndSection
 
Section "Screen"
    Identifier "Dual1"
    Device "Dual1"
    Monitor "Dual1"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1024x768_v"
    EndSubsection
EndSection

Section "Screen"
    Identifier "Dual2"
    Device "Dual2"
    Monitor "Dual2"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1024x768_s"
    EndSubsection  
EndSection
    
Section "ServerLayout"
    Identifier  "Dual"
    Screen 0 "Dual1"
    Screen 1 "Dual2" rightOf "Dual1"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

############################################################
#
# Fallback to the nv driver with main monitor at 1024x768
#
############################################################

Section "Device"
    Identifier "NV"
    VendorName "NV"
    Driver "nv"
    BusID  "PCI:1:0:0"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier  "NV"
    Device      "NV"
    Monitor     "ViewSonic P810"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "NV"
    Screen	"NV"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    Option "blank time"    "10"
    Option "off time"      "20"
EndSection



```

edit: spelling
edit: I may add that I think I have a fairly good understanding of the syntax of xorg.conf, and that averything seems to work. I just wonder about the ServerLayout part.

---

