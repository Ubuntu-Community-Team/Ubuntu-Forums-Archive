---
title: "Xinerama + nvidia + compiz-fusion"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by boluc91 on 2007-09-27
Hi all i have been trying to get compiz-fusion to work with xinerama.

I already managed to get twinview + compiz fusion reading trough a lot of posts and articles and it seems that the new nvidia drives screwed things up....

So basically i want to know if it would work with an older nvidia driver?
And also is there any alternative to xinerama that allows windows to switch desktop?

Some Specs:

Ubuntu feisty(E6600, asus P5B, 4 X 512 mb)(installed Xfce-desktop wich i use atm)
XFX GeForce 7300 GS
samsung syncmaster 931bw (1440x900)            DVI
some CRT (1600x1200 (wont mind if its lower))   VGA

Xfce 4.4.0

compiz-fusion 0.5.2
Emerald 0.3.0

Atm i use the nvidia proprietary drivers...




My xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1440 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "true"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "v4l" # Video for Linux	
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    #Load	   "dri"
    Load           "Xgl"
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
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "MED"
    HorizSync       30.0 - 98.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1280x960 +0+0; CRT: 1152x864 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBVisuals" "true"
    Option         "RenderAccel" "true"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1440x900 +0+0; DFP: 1280x800 +0+0; DFP: nvidia-auto-select +0+0"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBVisuals" "true"
    Option         "RenderAccel" "true"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "true"
EndSection

```



I hope you people know a way to get it to work.

Thanks for reading : )


EDIT:
What  i get when i start compiz:

bob@bobubuntu:~$ compiz --replace
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking for nVidia: present.
Checking for Xgl: not present.
Segmentation fault (core dumped)

---

