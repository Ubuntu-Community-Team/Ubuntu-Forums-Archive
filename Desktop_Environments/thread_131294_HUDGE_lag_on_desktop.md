---
title: "HUDGE lag on desktop"
date: 2006-02-16
forum: Desktop Environments
---

### Post by FatMom on 2006-02-16
HI !

So I have a little problem,my desktop lag. windows lag, scrolling web page lag, scrolling console lag all is lagging excepts games ! heres my config:

P3 933
512 SDRAM
g4 mx4000
80gb IDE

I have the lastest Nvidia drivers, and been searching for 3 days why is my desktop always lagging like I had no drivers, but games like quake3 works A1.

heres my xorg.conf:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "ca"
    Option         "XkbVariant" "fr"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "KDS XF-9p"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Monitor        "KDS XF-9p"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

THX !

---

### Post by linkunderscore on 2006-02-16
nvm

---

### Post by soonindallas on 2006-02-16
or just m

---

### Post by FatMom on 2006-02-16
??

---

### Post by FatMom on 2006-02-16
no one can help ? :(

---

