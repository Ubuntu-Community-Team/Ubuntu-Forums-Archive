---
title: "Error with Beryl compat check"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by cudds on 2007-08-21
Hey guys,

I run Gnome and Beryl at work fine - but I'm trying to get that magic at home.
At home I run KDE as I find it a bit faster on my laptop.

When I run beryl I get the following output
[I]
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on displ[/I]ay :0.0


I don';t really know what XFree86-DRI is! Can someone help me?

Hightlights of xorg.conf

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graph
ics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option  "XAANoOffscreenPixmaps"
        VideoRam        65536
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vs
ync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graph
ics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection


Thanks in advance - please let me know if you need more info

---

### Post by cudds on 2007-08-22
more on this - compiz blows the same error!

---

