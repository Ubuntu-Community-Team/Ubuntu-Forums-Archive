---
title: "How force ubuntu 9.04 to start with changed xorg.conf"
date: 2009-06-14
forum: General Help
---

### Post by nipponeon on 2009-06-14
I installed ubuntu 9.04 on my computer with an Intel mini-ITX board. So far so good.
Known problem with these boards is the SIS graphics.
There always was an easy workaround: change the driver settings in xorg.conf from "SIS" to "VESA".
It also works fine this time. 
Only problem is that when booting, ubuntu seems to know that I changed the xorg.conf file and insists on reconfiguring the graphics settings.
There is a start option offered to use my "wrong" settings, but this is not a very elegant way to start your computer.

Is there a way to force ubuntu to use my changed xorg.conf at startup ?

I put this in my xorg.conf: (works fine)

Section "Device"
    Identifier    "Generic Card"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-71
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" 
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier            "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
EndSection

---

