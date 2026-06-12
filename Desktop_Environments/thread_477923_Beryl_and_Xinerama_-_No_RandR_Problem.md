---
title: "Beryl and Xinerama - No RandR Problem"
date: 2007-06-18
forum: Desktop Environments
---

### Post by spivee69 on 2007-06-18
I've been searching the forums here and elsewhere and have found several references to this issue, but no resolutions. 

I'm currently running Edgy with Beryl 0.2.1.  I have two Nvidia 7600 Video cards, each are dual headed (one VGA, one HDMI) using the Nvidia GLX Driver 1:1.0.9631+2.6.20.5-16.28.  I'm trying to create one large desktop across three monitors, and have beryl enabled.  

I've had some success.  I was able to get Beryl working with TwinView across two monitors.  I have also been able to get all three monitors working as a single desktop (sorta, defined below) using TwinView and Xinerama combined, but with Xinerama, Beryl doesn't work.  When I try to start Beryl, it immediately fails back to metacity.  If I try to start Beryl from the command line, I get "Checking for RandR extension : failed.  No RandR extension"

If I disable Xinerama, Beryl will work fine, but I can only span two monitors, not all three.

Here are the view sections of my xorg.conf.  This configuration works with the three monitors spanned, but Beryl crashes.

```


########################################################
#  Screens Section for TwinView
########################################################

Section "Monitor"
    Identifier     "Sceptre"
    ModelName      "X22WG-Gamer"
    DisplaySize     380    305
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Fuji"
    ModelName      "FP-988D"
    DisplaySize     474    296
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Samsung"
    ModelName      "SyncMaster 226BW"
    DisplaySize     474    296
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

########################################################
#  Devices Section - One per Dual Head Card
########################################################

Section "Device"
    Identifier     "GPU-0"
    Driver         "nvidia"
    VendorName     "EVGA"
    BoardName      "7600GT" 
    Option         "RenderAccel"   "True"
    Option         "TwinView"
    Option         "TwinViewOrientation"   "RightOf"
    Option         "MetaModes"             "1680x1050, 1680x1050"
    Option         "ConnectedMonitor"      "DFP-0"
    Option         "UseEdidFreqs"          "True" 
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "GPU-1"
    Driver         "nvidia"
    VendorName     "EVGA"
    BoardName      "7600GT"
    Option         "RenderAccel"           "True"
    Option         "TwinView"
    Option         "TwinViewOrientation"   "LeftOf" 
    Option         "MetaModes"             "1680x1050, 1280x1024"
    Option         "ConnectedMonitor"      "CRT-0, DFP-0"
    Option         "UseEdidFreqs"          "True"
    BusID          "PCI:7:0:0"
EndSection

########################################################
#  Screens Section for TwinView
########################################################

Section "Screen"
    Identifier     "Center"
    Device         "GPU-0"
    Monitor        "Sceptre"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Right"
    Device         "GPU-0"
    Monitor        "Fuji"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Left"
    Device         "GPU-1"
    Monitor        "Samsung"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

##################################
# Layout Section
##################################

Section "ServerLayout"
    Option         "Xinerama"
    Identifier     "Default Layout"
    Screen         0 "Center" 0 0  
    Screen         1 "Right" LeftOf "Center"
    Screen         2 "Left" LeftOf "Right"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

```

Any help would be appreciated.  I'm not sure what I'm missing here, assuming that this is even possible.  

What I meant by the 'sorta' above, the desktop appears to be one large desktop, but if I set a screensaver, it runs spanning the two monitors running off the first monitor, but runs independently on the other monitor.  No big deal, but odd..

---

