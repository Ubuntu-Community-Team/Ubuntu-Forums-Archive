---
title: "Dual Screen Different Resolution Xinerama - 3D rendering"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by All3x on 2007-10-20
Hi

Spec: MSI Notebook S-271, AMD Turion 64TL, 1 Gb, ATI Xpress Radeon 1150, Gutsy

I've managed to have the dual screen working with 2 screens that have different resolution: 1200x800 (laptop) and 1280x1024 (external LCD) and enabled xinerama. Everything works fine except two things that might be linked:
- The 3d is working on the laptop screen but not the LCD
- On the LCD my mouse looks like a weird big black square

Could anyone help me with that? I'm becoming crazy about it...

Thx a lot

Here is my xorg.conf:

[I]Section "ServerLayout"
    Identifier          "Default Layout"
        Screen         "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
    InputDevice        "Generic Keyboard"
    InputDevice        "Configured Mouse"
    InputDevice        "Synaptics Touchpad"
        Option        "Xinerama" "on"
EndSection

Section "Files"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "vbe"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "fr"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ImPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    Option        "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]"
    Option        "DPMS"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
    Option        "VideoOverlay" "on"
    Option         "DesktopSetup" "horizontal,reverse"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
    Option        "VideoOverlay" "on"
        Screen 1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[1]"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
        Modes    "1200x800"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]"
    Device     "aticonfig-Device[1]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
        Modes    "1280x1024"
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
    Option        "Composite" "0"
EndSection
[/I]

---

### Post by All3x on 2007-10-22
Direct rendering is enabled but works only when Xinerama is disabled. Is there any way to enable them both?

Thx for any help or suggestion

---

