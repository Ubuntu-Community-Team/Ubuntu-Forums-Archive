---
title: "Debugging 3D games"
date: 2007-09-04
forum: Gaming &amp; Leisure
---

### Post by lhoffmeyer on 2007-09-04
Hey all,

What steps can I take to help me debug problems I am having with 3D games?

warzone2100 and padman load fine but freeze up my computer within 5-20 minutes after playing. I have to do a hard reboot.   Other 3D games seem to play
fine (Blobby, Neverball)

 I have a feisty/gutsy hybrid.
AMD Athlon(tm) 64 Processor 3000+
Radeon X850Pro
Using ATI restricted driver and fglrx

Using generic 386 kernel and not amd64 kernel

Section "Module"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc101 "
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection


Section "Device"
        Identifier      "ATI Technologies Inc R480 [Radeon X850Pro]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-80
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc R480 [Radeon X850Pro]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1600x1200"     "1280x768"      "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666

---

