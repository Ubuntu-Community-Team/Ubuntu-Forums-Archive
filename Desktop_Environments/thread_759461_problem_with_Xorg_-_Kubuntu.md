---
title: "problem with Xorg - Kubuntu"
date: 2008-04-19
forum: Desktop Environments
---

### Post by kikkertje on 2008-04-19
Hi,
Yesterday I was having a problem when I was uninstalling the Lamp-server trough Tasksell,
he started removing every component of the kubuntu-desktop.
The only way i could think of to repair, was to reinstall te kubuntu-desktop package via apt-get. All seemed to work well, until I rebooted and i received the following error.

[[IMG]http://img175.imageshack.us/img175/4294/snapshot1qc9.th.png[/IMG]](http://img175.imageshack.us/my.php?image=snapshot1qc9.png)

does someone knows how to solve this?

thank you

K

---

### Post by PmDematagoda on 2008-04-19
Post the output of:-
```
cat /etc/X11/xorg.conf
```
Also post the specifications of your PC.

---

### Post by kikkertje on 2008-04-19
```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
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
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection


```

System specification:

DELL INSPIRON 6400
2GB RAM
ATI MOBILITY RADEON X1400
Intel Centrino Duo 1.86Ghz

---

### Post by PmDematagoda on 2008-04-19
Open the xorg.conf file for editing using:-
```
sudo nano /etc/X11/xorg.conf
```
and then edit the last line to make it look like this:-
```
Section "Extensions"
        Option          "Composite"     "**1**"
EndSection
```
Save the file and then try again.

---

### Post by kikkertje on 2008-04-19
Ok, The error popup is gone.
Thank you very much

---

