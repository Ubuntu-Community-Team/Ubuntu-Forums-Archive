---
title: "Beryl windows borders problem. Tried everything"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by corrosion on 2008-03-04
Hi all,

It is not the first time I install a desktop with Beryl. This particular computer have some strange problem, and I think I need your help.
As described by title, no window borders. Machine haves nvidia video card.

Ubuntu is 7.10 32bit version. Nvidia is 7300go. processor core2duo. (A200-12X laptop)

No dri or glcore. DefaultDepth is 24. Extra options on "Device" section are there...

This is xorg.conf.

> Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
        Option          "XkbVariant"    "cat"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "RenderAccel" "True" #wrote by me
        Option          "AllowGLXWithComposite" "True" #wrote by me
        Option          "backingstore"  "True" #wrote by me
        Option          "TripleBuffer"  "True" #wrote by me
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-64
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
Option "AddARGBGLXVisuals" "True" #wrote by me
Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x800"
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
        Inputdevice     "Synaptics Touchpad"
EndSection

#Section "DRI"
#       Mode    0666
#EndSection
#
Section "Extensions" #wrote by me
Option "Composite" "True" #wrote by me
EndSection #wrote by me

Thank you very much for any help.

---

### Post by uberlube on 2008-03-04
I believe you have to enter something in the command line like 'disable emerald' or something. Its a workaround but not a fix.

---

### Post by corrosion on 2008-03-04
Thanks for your answer.
I tried it to but does not work. I tried before to use under beryl the GTK decorator but no working too.:confused:

---

### Post by joshrobinson on 2008-03-04
> **uberlube said:**
> I believe you have to enter something in the command line like 'disable emerald' or something. Its a workaround but not a fix.

hold ALT and hit F2, type
metacity --replace

[http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/]("http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/")

follow this little tutorial, to install compiz-fusion-icon
when its installed launch it with fusion-icon
this will let you select your window decorator, so you can find one that works for you

make sure you have emerald installed!

---

### Post by corrosion on 2008-03-04
Thank you but the URL you gave is not working. Anyway, I use the Beryl Manager to choose window decorators. No problem to choose metacity or compiz (compiz works correctly)

---

