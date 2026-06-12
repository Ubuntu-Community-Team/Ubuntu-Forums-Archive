---
title: "problems with compiz"
date: 2008-04-04
forum: Desktop Effects &amp; Customization
---

### Post by bdawg on 2008-04-04
I installed gutsy on my desktop a few days ago; I'm totally new to Linux. When I try to enable the custom visual effects, I get "visual effects cannot be enabled." My video card is an S3 Prosavage KM133, with "savage" as the driver. Entering compiz at the terminal gives:
 ```
myname@mycomputer:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 5333:8a26 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 
```
I already installed xgl. My xorg.conf file reads:
```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "S3 Inc. ProSavage KM133"
        Driver          "savage"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "G19LWk"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. ProSavage KM133"
        Monitor         "G19LWk"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

So, how do I get compiz working? I assume I have to edit xorg.conf, but I don't want to screw up my system.

---

### Post by tamoneya on 2008-04-04
Its probably because you only have 32 MB of Graphics RAM.  This is not enough for graphics intensive programs like compiz.  To fix this get a Nvidia PCI or PCIe card.  Id say a hi 7 series or low 8 series card should be good.  Try to steer clear of ATI since it doesnt work as well with linux.

---

### Post by bdawg on 2008-04-05
I was afraid of that. Out of curiosity, how did you know the specs on my video card? Also, what kind of specs are necessary for the cool compiz fx?

---

### Post by tamoneya on 2008-04-05
i just quickly googled your card and found another forum post where they guy posted his gfx memory.  As for how much is required i dont know.  I have 128 MB and i am running very smoothly and this in on a laptop.  any new desktop card should have close to 128 at this point so you should be all set.

---

