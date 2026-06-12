---
title: "Can one make Compiz-Fusion &quot;Xinerama&quot; Aware?"
date: 2007-07-30
forum: Desktop Environments
---

### Post by Metheos on 2007-07-30
By Default, the nvidia drivers when in Twinview mode send xinerama information to the window manager which it uses to determine proper placement of windows and maximization to the correct individual screen. Why doesn't compiz-fusion understand this information? Is there a way to make it understand it? Metacity understands the language, but compiz-fusion doesn't like to play nice with the other kids.

Running Ubuntu Feisty 7.04, Compiz Fusion from Trevino's repository.

---

### Post by Metheos on 2007-07-31
Figured it out, have to have the "Detect Outputs" box checked in the "General Settings"

---

### Post by ZoekDribbel on 2007-10-25
I got it working, and with 'it' i mean:

* Dual screen (2 monitors connected to my 7600GS via dvi and vga)
* Twinview
* Xinerama (yes, window do maximise correctly!)
* Compiz-fusion (wobbly all the way, cub rotating, etc)

Seems like enabling ```
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
``` did the trick some where.

Strangely Xinerama is set to zero (false?)
```
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection
```

What my xorg.conf looks like:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "NFC 171M"
    HorizSync       30.0 - 80.0
    VertRefresh     58.0 - 75.0
    Option         "DPMS"
EndSection
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```


Many thx to this thread: [http://www.suseforums.net/index.php?showtopic=40880&mode=linear](http://www.suseforums.net/index.php?showtopic=40880&mode=linear)

---

### Post by Meson on 2007-10-27
> **ZoekDribbel said:**
> Strangely Xinerama is set to zero (false?)
I think TwinView runs it's own Xinerama - I don't know if I'm wording that right but the actual Xinerama support needs to be turned off.  TwinView will do what it needs.

---

