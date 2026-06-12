---
title: "Dual Video Cards/Dual Monitors"
date: 2006-07-03
forum: Desktop Environments
---

### Post by soop on 2006-07-03
Hi, I'm trying to configure X to support dual displays to no avail. It's proving to be a pain in my *** actually.

Any Ideas/Suggestions? I'm running dual ATI Radeon X1300 PCI-E.

Anyone know where I can go in the right direction?

I tried the following settings:


Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen      1  "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


So If anyone has any ideas let me know ....

Thanks

---

### Post by yager on 2006-07-15
In case you have not been successful, try the HOWTO at the following link.

[http://www.ubuntuforums.org/showthread.php?t=162363&highlight=mergedfb+howto](http://www.ubuntuforums.org/showthread.php?t=162363&highlight=mergedfb+howto)

I am not an expert in this area, but from the description of this thread, you are more likely to find your expert there.

---

### Post by Ocxic on 2006-07-15
Your device section shoud have a bus id like this:

Section "Device"
        Identifier      "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"   <----you need this line
EndSection


you can find this bus id by type "lshw" in a terminal, just scroll through the results till you fins you video card.

---

### Post by jecos on 2006-07-15
Fglrx doesn't support running two ati cards at the moment. And That came straight from Matthew of ATI.  Running DualHead should be no problem on one of them.

---

