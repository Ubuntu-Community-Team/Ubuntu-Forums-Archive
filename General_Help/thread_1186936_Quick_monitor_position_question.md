---
title: "Quick monitor position question"
date: 2009-06-14
forum: General Help
---

### Post by PurposeOfReason on 2009-06-14
I have a dual monitor setup, one screen rotated. They are physically put like this
```

-------
|        |
|        |
|        | -------------
|        |                |
------- -------------

```

but xorg has them like this

```

-------  -------------
|        |                  |
 |        | -------------
|        | 
|        |      
------- -

```

How would I go about lowering the position of the right monitor?

---

### Post by cariboo on 2009-06-14
Moved to general help

---

### Post by CatKiller on 2009-06-14
I think it depends how you've generated your dual-screen setup. When I had two monitors set up (a long time ago, by defining two Screen entries in xorg.conf) I used ```
     Screen 1     "Screen1"     Relative "Screen0"     1280 256
``` in the ServerLayout section to align the bottoms of the screens, since one (Screen0) was 1280×1024 and the other (Screen1) was 1024×768.

I have no idea if this will work with the newer ways of setting up dual-monitors, but it might be worth a try.

---

### Post by PurposeOfReason on 2009-06-14
Thanks, it can be done that way, I'm just trying to figure out how I would do it because in my position, screen0 is too high as screen one is rotated.

Screen 0 "Screen0" 0 0
Screen 1 "Screen1" LeftOf "Screen0

I'm going to try negative values in the 0 0 part of Screen0 and see what happens.

---

### Post by CatKiller on 2009-06-14
Why not just have the non-rotated screen as your primary screen and define the rotated screen Relative to that?

---

### Post by PurposeOfReason on 2009-06-14
That is how it is. Screen0 is on the right, in 1680x1050 resolution. Screen1 is on the left, rotated to 1050x1680. But I see what you're saying. I could make the rotated primary and have the normal one relative 1050 pixels over. Just tried it, same problem still.

That didn't work, but I did get a breakthrough, it now lines up right, but only because the normal monitor is now at 1680x1680. I'm not sure why though, this is my xorg.conf
```

Section "ServerLayout"
    Identifier     "Dual Head Configuration"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    ModulePath      "/usr/lib64/xorg/modules"
    FontPath        "/usr/share/fonts/misc/"
    FontPath        "/usr/share/fonts/TTF/"
    FontPath        "/usr/share/fonts/OTF"
    FontPath        "/usr/share/fonts/Type1/"
    FontPath        "/usr/share/fonts/100dpi/"
    FontPath        "/usr/share/fonts/75dpi/"
    FontPath        "/usr/share/fonts/terminus/"
EndSection



Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "gb"
    Option         "XkbModel" "pc105"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2209WA"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
 #   Option     "RandRRotation" "on"
#    Option     "Rotate"        "CW"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2209WA"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option      "RandRRotation" "on"
    Option      "Rotate"        "CCW"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1680x1050 +0+630"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by CatKiller on 2009-06-14
> **PurposeOfReason said:**
> I could make the rotated primary and have the normal one relative 1050 pixels over.

And 630 pixels **down**. The *x* and *y* coordinates are counted from the top left corner and increase to the right and downwards, respectively.

---

### Post by CatKiller on 2009-06-14
I'd change this
```

Section "ServerLayout"
    Identifier     "Dual Head Configuration"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

```to this

```

Section "ServerLayout"
    Identifier     "Dual Head Configuration"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" Relative "Screen0" -2730 630
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

```Well, actually, I wouldn't. I'd change it to this.

```

 Section "ServerLayout"
     Identifier     "Dual Head Configuration"
     Screen      0  "Screen1" 0 0
     Screen      1  "Screen0" Relative "Screen0" 1050 630
     InputDevice    "Keyboard0" "CoreKeyboard"
     InputDevice    "Mouse0" "CorePointer"
 EndSection
 
```But only because it's neater. Although then the login window might be messed up. So maybe it isn't neater, after all.

---

### Post by PurposeOfReason on 2009-06-14
Thanks, I ended up doing the first one. I had to change which monitor and device went with what, but it worked in the end. And just to be picky, though I don't expect it to work, do you know if it is possible for if I'm at the top of the left monitor and move the mouse over, it doesn't because technically there isn't any screen there? At the moment it just moves to the top of the other screen. Not really a big thing, but if it's possible.

---

### Post by CatKiller on 2009-06-14
Not as far as I know. It's one of the things that annoyed me about dual monitors of different resolutions; that you'd move the mouse pointer from the top of one screen to the other and then back again, and the mouse pointer would jump however many pixels it was downwards.

---

