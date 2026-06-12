---
title: "Displaylink USB, the screen is work but show Logo only"
date: 2012-10-08
forum: Desktop Environments
---

### Post by khoaofgod on 2012-10-08
I tried with this problem for 2 years already. LOL, today, I install Ubuntu for I have to resolve it or I will back to stupid Windows 7.

First, I have 3 monitors. My graphic card is support dual ( ATI Radeon ), so I have no problem on extend those multi monitor on VGA and DVI.

The 3rd monitor is Displaylink USB. 
After installed everything required, when I reboot, the displaylnk monitor show "Ubuntu ...." like logo / loading screen.

I go to System > Display , Detect monitor, it only show my 1st and 2nd, NO 3RD Displaylink.

I can move my mouse between those 1st & 2nd, but the 3rd is only show the Ubuntu Screen.

I press CTRL + ALT + 1, then screen switch to Displaylink USB 3RD monitor, but its "Terminal" not a desktop. 

Then I press CTRL + ALT + 7 , the screen switch back to my 1st, 2nd, and the displaylink 3rd is witch back to Logo / Ubuntu again.

This is my /etc/X11/xorg.conf


```
    Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen      1  "DisplayLinkScreen" Leftof "aticonfig-Screen[0]-0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
    EndSection
    
    Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
    EndSection
    
    Section "Module"
        Load  "glx"
        Load  "dri2"
        Load  "dbe"
        Load  "dri"
        Load  "record"
        Load  "extmod"
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
        Identifier   "aticonfig-Monitor[0]-0"
        Option        "VendorName" "ATI Proprietary Driver"
        Option        "ModelName" "Generic Autodetecting Monitor"
        Option        "DPMS" "true"
    EndSection
    
    Section "Monitor"
        Identifier   "DisplayLinkMonitor"
    EndSection
    
    Section "Monitor"
        Identifier   "0-DFP1"
        Option        "VendorName" "ATI Proprietary Driver"
        Option        "ModelName" "Generic Autodetecting Monitor"
        Option        "DPMS" "true"
        Option        "PreferredMode" "1680x1050"
        Option        "TargetRefresh" "60"
        Option        "Position" "0 0"
        Option        "Rotate" "normal"
        Option        "Disable" "false"
    EndSection
    
    Section "Monitor"
        Identifier   "0-CRT2"
        Option        "VendorName" "ATI Proprietary Driver"
        Option        "ModelName" "Generic Autodetecting Monitor"
        Option        "DPMS" "true"
        Option        "PreferredMode" "1920x1080"
        Option        "TargetRefresh" "60"
        Option        "Position" "1680 0"
        Option        "Rotate" "normal"
        Option        "Disable" "false"
    EndSection
    
    Section "Device"
    
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "NoAccel"                # [<bool>]
            #Option     "SWcursor"               # [<bool>]
            #Option     "Dac6Bit"                # [<bool>]
            #Option     "Dac8Bit"                # [<bool>]
            #Option     "BusType"                # [<str>]
            #Option     "CPPIOMode"              # [<bool>]
            #Option     "CPusecTimeout"          # <i>
            #Option     "AGPMode"                # <i>
            #Option     "AGPFastWrite"           # [<bool>]
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
            #Option     "IgnoreEDID"             # [<bool>]
            #Option     "CustomEDID"             # [<str>]
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
            #Option     "RenderAccel"            # [<bool>]
            #Option     "SubPixelOrder"          # [<str>]
            #Option     "ClockGating"            # [<bool>]
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
            #Option     "DefaultTVDACAdj"        # [<bool>]
            #Option     "Int10"                  # [<bool>]
            #Option     "EXAVSync"               # [<bool>]
            #Option     "ATOMTVOut"              # [<bool>]
            #Option     "R4xxATOM"               # [<bool>]
            #Option     "ForceLowPowerMode"      # [<bool>]
            #Option     "DynamicPM"              # [<bool>]
            #Option     "NewPLL"                 # [<bool>]
            #Option     "ZaphodHeads"            # <str>
        Identifier  "Card0"
        Driver      "radeon"
        BusID       "PCI:5:0:0"
    EndSection
    
    Section "Device"
    
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "ShadowFB"               # [<bool>]
            #Option     "Rotate"                 # <str>
            #Option     "fbdev"                  # <str>
            #Option     "debug"                  # [<bool>]
        Identifier  "Card1"
        Driver      "fbdev"
        BusID       "PCI:5:0:0"
    EndSection
    
    Section "Device"
    
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "ShadowFB"               # [<bool>]
            #Option     "DefaultRefresh"         # [<bool>]
            #Option     "ModeSetClearScreen"     # [<bool>]
        Identifier  "Card2"
        Driver      "vesa"
        BusID       "PCI:5:0:0"
    EndSection
    
    Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option        "Monitor-DFP1" "0-DFP1"
        Option        "Monitor-CRT2" "0-CRT2"
        BusID       "PCI:5:0:0"
    EndSection
    
    Section "Device"
        Identifier  "DisplayLinkDevice"
        Driver      "displaylink"
        Option        "fbdev" "/dev/fb1"
        Option "ShadowFB" "off"
    EndSection
    
    
    Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        DefaultDepth     24
        SubSection "Display"
            Viewport   0 0
            Virtual   3600 1920
            Depth     24
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier "DisplayLinkScreen"
        Device     "DisplayLinkDevice"
        Monitor    "DisplayLinkMonitor"
        DefaultDepth     24
        SubSection "Display"        
            Depth     24
            Modes    "1920x1080"
        EndSubSection
    EndSection
```

---

