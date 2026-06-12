---
title: "Dual Monitors with TwinView"
date: 2006-06-27
forum: Desktop Environments
---

### Post by earle on 2006-06-27
Hi there..   I'm having a problem getting dual monitor support working properly.

I have an Nvidia card, and am using TwinView.  I can get everything working properly, but only at 1024x768!!  I can increase to 1280x1024 on a single monitor just fine, but then nothing else works.     When I try increasing my MetaMode to "1280x1024,1280x1024" and my Virtual to 2560x1024 it doesn't work!  Any ideas?

Thanks in advance


Identifier "device1"
        VendorName "nVidia Corporation"
        BoardName "NVIDIA GeForce FX (generic)"
        Driver "nvidia"
        Option "DPMS"
        Option "NoLogo" "TRUE"
        Option "HWCursor" "TRUE"
        Option "CursorShadow" "TRUE"
        Option "CursorShadowAlpha" "75"
        Option "CursorShadowXOffset" "10"
        OPtion "CursorShadowYOffset" "5"
        Option "RenderAccel" "TRUE"
        Option "AllowGLXWithComposite" "TRUE"
        Option "TwinView" "TRUE"
        Option "SecondMonitorHorizSync" "28-61"
        Option "SecondMonitorVertRefresh" "48-90"
        Option "TwinViewOrientation" "LeftOf"
        Option "MetaModes" "1024x768,1024x768"
EndSection

Section "Monitor"
    Identifier     "monitor1"
    Option         "DPMS"
EndSection

Section "Screen"
        Identifier "screen1"
        Device "device1"
        Monitor "monitor1"
        DefaultColorDepth 24

        Subsection "Display"
                Depth 8
                Virtual 2048 768
        EndSubsection

        Subsection "Display"
                Depth 15
                Virtual 2048 768
        EndSubsection

        Subsection "Display"
                Depth 16
                Virtual 2048 768
        EndSubsection

        Subsection "Display"
                Depth 24
                Virtual 2048 768
        EndSubsection
EndSection

Section "ServerLayout"
Identifier "layout1"
InputDevice "Generic Keyboard" "CoreKeyboard"
InputDevice "Configured Mouse" "CorePointer"
Screen "screen1"
EndSection

---

