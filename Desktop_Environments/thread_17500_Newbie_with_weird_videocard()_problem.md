---
title: "Newbie with weird videocard(?) problem"
date: 2005-02-28
forum: Desktop Environments
---

### Post by Seazzy on 2005-02-28
I have installed ubuntu on my PC (Celeron, 128mb RAM, Aladin tnt2 on board video card.) It works fine in every way except that it occasionally freezes. Usually this happens when I a)try to move a file or folder into another file in the home directory GUI, b)do anything involving text boxes in Firefox (especially when using the text box scrollbar).

Here is my XF86Config-4 file:

```
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"

EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "dvorak"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
   Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV5 [Aladdin TNT2]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Visual Sensa"
        HorizSync       30-70
        VertRefresh     50-160
Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV5 [Aladdin TNT2]"
        Monitor         "Visual Sensa"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"

                Depth           8
                Modes            "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection    SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

And that's all I know. Can anyone help me solve this mystery?

I originally posted this thread in the wrong section, you can read it at [http://ubuntuforums.org/showthread.php?t=16934](http://ubuntuforums.org/showthread.php?t=16934) .

---

