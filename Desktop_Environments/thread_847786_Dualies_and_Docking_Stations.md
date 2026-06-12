---
title: "Dualies and Docking Stations"
date: 2008-07-02
forum: Desktop Environments
---

### Post by beekus on 2008-07-02
Howdy Folks.  I've been using Ubuntu since November on a dual boot machine and almost exclusively for the last couple of months.  It is really a sweet OS and the community is phenomenal.  I've been able to figure out almost everything by just searching forums.  This is my first post, and it is regarding the one thing I haven't been able to figure out on my own.

I have a Thinkpad T61P and have had difficulty getting some dual monitor action going.  I've messed with all the settings in nvidia-settings.  I'm so close though.  Currently I have two separate xorg.conf files, and I switch them manually depending on whether I am docked (dual monitor) and when I'm undocked.  Then, of course, I restart gnome with ctrl-alt-backspace.

Ideally, I would like to create a script that somehow detects if I am in the dock, and uses the appropriate xorg.conf.  I need help with:

1)How would I determine if I am in the dock?
2)Where is the most appropriate place to run such a script?

It really isn't that big of a deal, as I usually only remove it from the dock when I am going home from work for the evening, but I have to believe it's possible!

Thanks in advance for the help.

---

### Post by Bultot on 2008-08-13
*bump*

I´m thinking about buying a thinkpad t61p too beceause of the docking station. I´d really like to know how to use it for external dual head purpose. (no notebook screen, 2 LCD)
When connected to the dock, use two external monitors.
I´d like to see the solution with the detection too..

btw: I read that you can use a PCI Express video card in the dock, but only half-size. Which one is half size and has dual dvi out (nvidia) ?
Does it work with linux?

Thanks in advance

---

### Post by ElMonoGrande on 2008-08-13
Bekus,
Here is the xorg.conf that I use with my Dell Latitude D630. It has an nVidia Quadro NVS 135M in it. I have it docked and use the laptop monitor and external LCD at the same time with 2 completely separate desktops in KDE. Under Gnome, I can't get the configuration options that I can under KDE so your mileage may very as to what you can and can't do. Hope this helps.


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
#    Option         "StandbyTime" "15"
#    Option         "SuspendTime" "30"
#    Option         "OffTime" "45"
EndSection

Section "Files"
    RgbPath      "/usr/lib/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath 	"/usr/share/fonts/truetype"
    FontPath    "/usr/share/fonts/X11"
EndSection

Section "Module"
    Load         "dbe"
    Load         "extmod"
    Load         "type1"
    Load         "freetype"
    Load         "GLcore"
    Load         "glx"
    Load         "record"
    Load         "xtrap"
    Load         "dri"
    Load         "type1"
    Load         "freetype"
    Load         "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Extensions"
    Option  "Composite"  "Enable"
EndSection

Section "InputDevice"
    # generated from data in "/etc/conf.d/gpm"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

#Section "InputDevice"
#   Driver      "synaptics"
#   Identifier  "TouchPad"
#   Option      "SendCoreEvents"
#   Option      "Protocol" "auto-dev"
#   Option      "SHMConfig" "on"
#EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2007FP"
#    HorizSync       30.0 - 83.0
#    VertRefresh     56.0 - 76.0
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 130.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"	
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
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
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

