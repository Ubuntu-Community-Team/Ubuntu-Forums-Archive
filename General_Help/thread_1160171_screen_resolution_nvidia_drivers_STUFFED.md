---
title: "screen resolution nvidia drivers STUFFED"
date: 2009-05-15
forum: General Help
---

### Post by Vigh on 2009-05-15
hey, i am relatively speaking a noob to ubuntu, and have been trying to set up my geforce4 420 go 32mb graphics card on my TOSHIBA satellite 6100 p4 mobile laptop for the last 3 days without success, i have searched and searched both google and ubuntu forums without success. i am running ubuntu 9.04, current drivers are legacy drivers 96.43.10, my problem is low screen resolutions 800x600 max in nvidia-settings window, i have tried editing the xorg.conf file and it does not solve the problem, the xorg.conf as is at the moment is as follows-

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24      Option  "AddARGBGLXVisuals"     "True"
        Option  "UseDisplayDevice"      "DFP"
SubSection "Display"
Depth 24
Virtual 1024 768
Modes "1400x1050@60" "1200x800@60" "1024x768@60" "800x600@60" "640x480@50"
EndSubSection
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

---

