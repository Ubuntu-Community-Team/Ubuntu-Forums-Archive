---
title: "[Fluxbox] Set wallpapers on both monitors in dual setup?"
date: 2011-02-16
forum: Desktop Environments
---

### Post by Chrilleee on 2011-02-16
I have a dual setup and just switched from Xubuntus Xfce? to Fluxbox... But now I can't set wallpapers on both my screens anymore. How do I do that?
I had to change the Fluxbox menu from Head 1 to Head 2 to get it on my bigger, primary screen. Which is the one getting a wallpaper when I'm setting one.

Here's my xorg.conf:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen         "Screen0"
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
    Load  "dbe"
    Load  "dri"
    Load  "extmod"
    Load  "dri2"
    Load  "record"
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
    Identifier    "Monitor0"
    VendorName    "VSC"
    ModelName    "VX2435wm"
    HorizSync    30.0 - 82.0
    VertRefresh    50.0 - 76.0
    ModeLine    "1920x1200_60"    154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync
    Option        "DPMS"
    Option        "PreferredMode"    "1920x1200"
    Option        "LeftOf"    "Monitor1"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "DPMS"
    Option        "PreferredMode"    "1280x1024"
    Option        "RightOf"    "Monitor0"
EndSection

Section "Device"
    Identifier    "Card0"
    Driver        "radeon"
    BusID        "PCI:5:0:0"
    Option        "monitor-DVI-0" "Monitor0"
    Option        "monitor-VGA-0" "Monitor1"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Card0"
    Monitor        "Monitor0"
    Monitor        "Monitor1"
        DefaultDepth    24
    SubSection "Display"
        Depth    24
        Virtual 3200 1200
    EndSubSection
EndSection

```

---

