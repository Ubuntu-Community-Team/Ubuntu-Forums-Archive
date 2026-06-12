---
title: "newbie w/ resolution problem, inspiron 1100 laptop"
date: 2005-10-22
forum: Desktop Environments
---

### Post by wbsquared on 2005-10-22
hello, im new to the forums, trying to get the hang of this linux thing. 

My problem is that i can't change my resolution from 640x480. Im not sure how to fix this problem, but this resolution sucks as some of you may know. Im sorry to ask a question that many have asked before, but i couldn't find my answer and i need info spoon fed to me since im new. Help is very much appreciated.

//here is my etc/X11/xorg.conf

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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset$  
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset$        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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

### Post by aysiu on 2005-10-22
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by wbsquared on 2005-10-22
i checked out the link [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

Since i have an intel card and im sure that my resolution isn't delievered by the Vbios. So i ran this command:

sudo apt-get install 855resolution

//after running that command i get this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 855resolution

//so now i can't install the 855resolution patch...any suggestions. Anything im doing wrong. If at all possible talk to me like im 4, lol i can't stress my newness.

---

### Post by aysiu on 2005-10-22
There are other solutions on that page. I'd highly recommend the VertRefresh/ HorizSync one, since Ubuntu seems to have "recognized" your monitor as "generic." This is your code ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection
```

This is my code ```
Section "Monitor"
        Identifier      "VG150"
        HorizSync       30-62
        VertRefresh     50-70
        Option          "DPMS"
EndSection

``` Yours won't be the same ranges, but you get the picture, I hope.

However, if you want to install that package:

*To install 855-resolution on Ubuntu 5.10 make sure that you have includet the "universe" repository and type:*

Enable the "universe" repository by following the instructions here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then, try that command again.

---

### Post by wbsquared on 2005-10-25
i tried what you said ayisu, but i didn't work. So i went back to my theory of installing the 855resolution patch. I got that installed after installing ubuntu 5.10.

when i type in the following command:

sudo 855resolution -l

im supposed to get a readout such as this:

855resolution version 0.4, by Alain Poirier

Chipset: Unknown (id=0x25908086)
VBIOS type: 2
VBIOS Version: 3412

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1400x1050, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1400x1050, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1400x1050, 32 bits/pixel

Instead i get the following readout:

855resolution version 0.4, by Alain Poirier

Chipset: 845G (id=0x25608086)
Unknow VBIOS structure

---Any suggestions as to what i should do now, since my resolution is still at 640x480. And i know that this thread is prolly in the wrong section now that im running 5.10 and not 5.04

---

