---
title: "No 3d acceleration with xorg.conf"
date: 2017-04-01
forum: Desktop Environments
---

### Post by Frostwarrior on 2017-04-01
Hi everyone. I'm trying to create a custom Xorg.conf to handle the natural screen tearing that the propietary Nvidia driver has.

So I created a Xorg.conf using the old school way: ```
X -ac -configure
```

Passed it to **/etc/X11/** and while I have a X screen, no I have no 3d acceleration.

When I try **glxinfo**, this appears:
```
glxinfo
name of display: :0
Error: couldn't find RGB GLX visual or fbconfig
```

But when I delete my **xorg.conf**, X detects everything ok and I have 3d accel and glx.

Any ideas?
This is my Xorg.conf:
```
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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # <i>
    Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:1:0:0"
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
```

---

### Post by deadflowr on 2017-04-01
> I'm trying to create a custom Xorg.conf to handle the natural screen tearing that the propietary Nvidia driver has.
is the proprietary driver installed? Because you're xorg.conf file lists the nouveau driver.
If the nvidia driver is installed the nouveau driver gets blacklisted.
Then if the nouveau driver is listed in an xorg file it confuses the system.

---

