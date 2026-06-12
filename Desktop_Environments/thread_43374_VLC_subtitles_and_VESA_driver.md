---
title: "VLC subtitles and VESA driver"
date: 2005-06-21
forum: Desktop Environments
---

### Post by lool on 2005-06-21
Hello,
Yesterday I connected my HP Pavilion to TV. I installed atitvout package, changed xorg.conf (instead of "ati"  put "vesa"). Everything works OK besides subtitles in VLC. I tried different screen resolutions, etc. Nothing helped. When had changed driver to "ati" subtitles appeared correctly. With vesa subtitles do not appear even on LCD screen.

Please help me solve this issue!!

best regards,
lool

----------------------------------
Here is my xorg.conf:
----------------------------------
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
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
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by RastaMahata on 2005-06-21
"Please do not post questions here. This is for HOWTO's and FAQs only."

I would love to help you, but you must post in the right forum (if you didnt find an answer with the search tool first).

Admins, please move this :(

---

