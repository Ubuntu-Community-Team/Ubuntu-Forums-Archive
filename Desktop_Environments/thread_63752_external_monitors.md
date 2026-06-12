---
title: "external monitors"
date: 2005-09-08
forum: Desktop Environments
---

### Post by locald on 2005-09-08
I have been trying to make my Dell Inspiron 6000 support external monitors/projectors. I have tried i810switch and i855crt but none of them works well. "i810switch crt on" enables the output to the external monitor but the quality is really poor. The top panel is invisiable and the entire display is flickering. "i855crt swcursor on 1024x768@85" gives me,

Intel 855GM CRT out driver V0.4
Copyright (C) Merello Andrea 2004

found mode 1024x768@85
No know videocard has been found.

This is the configuration for my screen in xorg.conf.

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Any suggestions and help are appreciated.

---

