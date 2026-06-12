---
title: "Dual monitors with beryl?!?"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by the_bob on 2007-05-07
I have a 15in and a 22in widescreen. I have got the monitors running great! I just cant seem to get beryl working. If a disable one or use twinview it works but with a tinny and a huge monitor twinview is hardly usable. I was wondering if anyone could help me out. I have tried to find help without posting but this time I'm at a loss.

here is my xorg conf file

[I][COLOR="DarkGreen"][B]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 369
    Screen      1  "Screen1" 1280 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMI eView 15w2"
    HorizSync       30.0 - 58.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer X221W"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x800 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection[/B][/COLOR][/I]

clean eh? thanks for the help.

---

### Post by rsambuca on 2007-05-07
It states explicitly in the Beryl documentation that it will not work with xinerama.  Perhaps you should try reading the documentation!

---

### Post by the_bob on 2007-05-07
sorry I cant get beryl to work with dual monitors and move things between the two. I read the doc jerk. I forgot to mention that I'd like the monitors to be usable together.

---

### Post by rsambuca on 2007-05-07
I'm trying to save you some time from messing around with xinerama and beryl at the same time and you are calling me a jerk????:( 

Yeah, good luck with that.

---

### Post by orb9220 on 2007-05-08
> I read the doc jerk.

If you had you would have seen as rsambuca stated it will not work with xinerama but only in twinview.

Sorry but with that kind of attitude does not motivate me to help you.

---

