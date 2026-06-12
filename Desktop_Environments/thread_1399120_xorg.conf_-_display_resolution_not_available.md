---
title: "xorg.conf - display resolution not available"
date: 2010-02-05
forum: Desktop Environments
---

### Post by CyberRascal on 2010-02-05
Hello. I am using xubuntu karmic koala. I am having trouble having my integrated intel graphics controller configured. By default I can choose 800x600 and 640x480. I want my monitor to run at 1024x768, since I know that it can handle it. I managed to get it to to run at 1024x768 for a while, when downloading a xorg.conf I found on the internet, however I cannot find it again, after a reinstall.

By default I have no xorg.conf. So I shutdown the x-server by X11/gdm stop, and ran Xorg -configure.

This yielded the following xorg.conf:

[PHP]
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri"
    Load  "dri2"
    Load  "glx"
    Load  "record"
    Load  "dbe"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82865G Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
[/PHP]

I modifed the following section

[PHP]
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
[/PHP]

To look like so

[PHP]
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1024x768"
    EndSubSection
[/PHP]

This changed nothing. How can I make 1024x768 show up as an alternative in display settings? One thing is it says Screen 1 in display settings, but the xorg.conf seems to pertain to screen 0?

---

### Post by CyberRascal on 2010-02-06
Sorry for the bump, but I was on page 4...

---

