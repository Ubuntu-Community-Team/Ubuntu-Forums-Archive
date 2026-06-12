---
title: "Gnome-Terminal Transparency and Compiz"
date: 2007-06-20
forum: Debian
---

### Post by kevinlyfellow on 2007-06-20
So I decided to do a netinstall with debian and didn't have wireless off the bat, so I started with a base system.

I got gnome installed and then compiz.  But the gnome-terminal still acts like its normal stupid self and does that pseudo transparency (which is just goofy imo).  Does anyone have any ideas on how I can fix that?  Here is my xorg.conf file

```

...

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        Load    "dbe"
EndSection

...

Section "Extensions"
        Option          "Composite"             "Enable
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "VBERestore"            "true"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
...
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Also, does anyone know how to put six sides on my "cube"?

Edit: Nevermind, went to arch

---

