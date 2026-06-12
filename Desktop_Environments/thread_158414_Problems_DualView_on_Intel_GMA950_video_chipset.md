---
title: "Problems DualView on Intel GMA950 video chipset"
date: 2006-04-11
forum: Desktop Environments
---

### Post by coolness1 on 2006-04-11
Hi,

i have a problem with a dell optiplex gx620 which contains a GMA950 video chipset...

I want to connect 2 17" TFTs without cloning the first tft to the second, so that the desktop will expand on the second tft.

Is there somebody who knows how it will work with this video chipset?

I have installed Ubunto 6.0.6.

Here is a short extract of xorg.conf file:

xorg.conf
----------------------------------------------------------------------------------
Section "Device"
        Identifier      "IntelLinks"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "IntelRechts"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1707FP"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "DELL 1706FPV"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "ScreenLinks"
        Device          "IntelLinks"
        Monitor         "DELL 1707FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "ScreenRechts"
        Device          "IntelRechts"
        Monitor         "DELL 1706FPV"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "DualHead"
        Screen 0        "ScreenLinks" 0 0
        Screen 1        "ScreenRechts" LeftOf "ScreenLinks"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "MonitorLayout" "LFP,DFP"
        Option          "Xinerama" "on"
        Option          "Clone" "off"
EndSection

Section "DRI"
        Mode    0666
EndSection

--------------------------------------------------------------------------------------------------

Can sombody help me???

Greets

Ramin****

---

