---
title: "Dual Monitors"
date: 2005-10-16
forum: Desktop Environments
---

### Post by programgeek on 2005-10-16
Is there a guide on how to get Dual Monitors working in Breezy?

MEANINGLESS-PLACED LYRICS:

[I]We get it almost every night
When that moon is big and bright
It's a supernatural delight
Everybody's dancing in the moonlight

Everybody here is out of sight
They don't bark and they don't bite

They keep things loose they keep it tight
Everybody's dancing in the moonlight

CHORUS

Dancing in the moonlight
Everybody's feeling warm and bright
It's such a fine and natural sight
Everybody's dancing in the moonlight

We like our fun and we never fight
You can't dance and stay uptight
It's a supernatural delight
Everybody's dancing in the moonlight

CHORUS

We get it almost every night
And when that moon is big and bright
It's a supernatural delight
Everybody's dancing in the moonlight

CHORUS (repeat to fade)[/I]

---

### Post by fimbulvetr on 2005-10-16
Not sure about howtos, my install picked mine up. If it's any help, here's my xorg.conf:

```

Section "Extensions"
#       Option "Composite"      "Enable"
        Option "RENDER"         "Enable"
#       Option "RANDR"          "Enable"
EndSection

Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

Section "Files"
        FontPath        "unix/:7100"      # local font server
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load        "bitmap"
    Load        "dbe"
    Load        "ddc"
    Load        "dri"
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
    Load        "int10"
    Load        "record"
    Load        "vbe"
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "dri"
    Load        "GLcore"
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    Driver      "kbd"
    Option      "AutoRepeat"    "500 5"
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "mouse"
    Option      "Protocol"      "IMPS/2"
    Option      "Device"        "/dev/input/mice"
        Option  "Buttons"       "5"
        Option  "ZAxisMapping"  "4 5"
EndSection

Section "Monitor"
    Identifier  "Generic Monitor"
    Option      "DPMS"
    HorizSync   30-81
    VertRefresh 60-60
EndSection

Section "Device"
        Identifier      "Intel"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        32768
EndSection

Section "Device"
        Identifier  "Nvidia"
        #Driver      "nvidia"
        Driver      "nv"
        VendorName  "videocard vendor"
        BoardName   "geforcemx"
        VideoRam    32768
        Option      "DPMS"  "on"
        Option      "RenderAccel"   "on"
        Option  "NvAGP" "2"
        BusID      "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Intel"
    Monitor     "Generic Monitor"
    DefaultDepth        16
    SubSection "Display"
                Depth           16
                Modes           "1280x1024"
                #Modes          "1152x870@75"
    EndSubSection
EndSection

Section "Screen"
        Identifier  "Screen 2"
        Device      "Nvidia"
        Monitor     "Generic Monitor"
        DefaultDepth        16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
                #Modes          "1152x870@75"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Dual"
        Screen "Screen 2"
        Screen "Screen 1" LeftOf "Screen 2"
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

