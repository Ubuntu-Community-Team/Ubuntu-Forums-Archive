---
title: "Making xorg.conf apply xrandr settings at startup"
date: 2008-08-02
forum: Desktop Environments
---

### Post by samsari on 2008-08-02
Hi guys, I may have been completely blind and missed something already posted, but I have done a bit of searching and not really found anything specific to my problem.

I'm actually using Arch, but I recall I had this exact same problem on Ubuntu as well. Unfortunately I don't remember how it got fixed.

Basically, what I have is an old laptop with a defunct screen (the backlight's gone) connected to my tv instead. The tv is an lcd tv with a maximum resolution of 1650x990 (or something like that) and is actually connected to the laptop with a VGA cable, so it's essentially an external monitor.

When xorg starts, it treats the laptop screen as the primary display and mirrors the desktop on the tv. The main problem is that in mplayer, the XV output can only be directed to one display at a time, and that is naturally defaulted to the primary display, so on the tv, I get a black box whenever I try and play a movie. Because the laptop screen is knackered, I have no need for it and so I would like some way to tell xorg to either ignore it and only use the VGA screen, or even set the tv as the primary display.

I have found the xrandr command which will turn off the laptop (LVDS) screen thereby making the tv the primary and this is perfect, but I have to manually run that command each and every time xorg starts up. What I'm looking for is something to put in xorg.conf that will do the same thing when xorg starts.

This is the command which turns off the laptop screen:
```
xrandr --output LVDS --off
```
And this is my xorg.conf
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/usr/share/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "dri"
    Load  "glx"
    Load  "record"
    Load  "extmod"
    Load  "GLcore"
#    Load  "dbe"
    Load  "xtrap"
    Load  "freetype"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      470   300    # mm
    Identifier   "telly"
    VendorName   "GSM"
    ModelName    "M228WA"
 ### Comment all HorizSync and VertRefresh values to use DDC:
    HorizSync    28.0 - 83.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
    Option    "Enable" "true"
EndSection

Section "Monitor"
    Identifier    "lappy"
    Option    "DPMS"
#    Option    "Ignore" "true"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "DDCMode"                # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "DynamicClocks"          # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon Mobility M6 LY"
    BusID       "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPSize" "16" # default: 8
        Option          "RingSize" "4"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "true"
        Option          "RenderAccel" "true"
        Option          "AccelMethod" "XAA" # or XAA, EXA
        Option          "DDCMode"
        Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "true"
        Option          "DynamicClocks" "true"
        Option          "bioshotkeys"   "True"
        Option      "DRI"     "true"
    Option     "VideoOverlay"    "on"
#    Option    "MonitorLayout"    "VGA"
        Option          "monitor-VGA" "telly"
        Option          "monitor-LVDS" "lappy"

EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "telly"
    DefaultDepth    24
#    SubSection "Display"
#        Viewport   0 0
#        Depth     1
#    EndSubSection
#    SubSection "Display"
#        Viewport   0 0
#        Depth     4
#    EndSubSection
#    SubSection "Display"
#        Viewport   0 0
#        Depth     8
#    EndSubSection
#    SubSection "Display"
#        Viewport   0 0
#        Depth     15
#    EndSubSection
#    SubSection "Display"
#        Viewport   0 0
#        Depth     16
#    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
 Group        "video"
 Mode         0666
EndSection
```

---

### Post by kagashe on 2008-08-28
Hi,

I am also using an external monitor because the Laptop screen is broken and using xrandr command. I have put this command to auto-execute after I login to GDM.

I think you can open sessions dialog and add it as an application. Since I don't use Gnome I can't guide you step by step.

kagashe

---

### Post by tekkenlord on 2009-01-28
Even though a bit late, the answer to your problem is the following:

Add to the "Device" section of the xorg.conf the following:

Option "monitor-LVDS" "LVDS"

and finally create a new "Monitor" section like this:

Section "Monitor"
       Identifier "LVDS"
       Option "Disable" "true"
EndSection


This works flawlessly for me. This is my xorg.conf if you need to compare.

Section "Device"
        Identifier      "Configured Video Device"
        Option "monitor-LVDS" "LVDS"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Monitor"
       Identifier "LVDS"
       Option "Disable" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

