---
title: "Multiple Resolutions 1 for Flatpanel another for TV"
date: 2006-06-25
forum: Desktop Environments
---

### Post by tworkemon on 2006-06-25
Hello, What i am trying to do is this. I have a Radeon 9600 card and I would like to have 2 main display resolutions, 1 for normal comp usage and second for when I want to watch TV it would be at a lower resolution. The TV-out works great i can see it on my tv but the resolution is too big so lowering it would fit the tv screen. I would like to have a shortcut key to change it when I would like ot watch a movie if possible. Your help would be greatly appreciated. Thanks in advanced !!

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```
```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver          "fglrx"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "SDM-HS73"
        Option          "DPMS"
        HorizSync       28-65
        VertRefresh     48-65
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Monitor         "SDM-HS73"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes        "1280x1024" "1024x768" "800x600"
       EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by pyromithrandir on 2006-06-25
ctrl+alt+keypad +/- will go through the resolutions in the "Modes" line.

---

### Post by tworkemon on 2006-06-25
Cool didnt know I could do that, I think i need to setup/add more resolutions cuz all of them are still too big for the TV. Too big as in it wont fit in the screen of the TV.

---

