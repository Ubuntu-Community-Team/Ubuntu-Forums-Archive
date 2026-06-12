---
title: "Gusty goes back to login screen when activating desktop effects?"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by LyricalK on 2007-11-18
Hi, i have downloaded and installed ubuntu 7.10 (gusty) and i tried to activate desktop effects but it wont work, every time i try to activate the effects it crashes and returns to the login screen and the resolution changes, today my resolution changed from 1400x900 to something very big that my screen wont display, so i had to take it downstairs and plug it into my 50" plasma to change the resolution, when i logged in the desktop effects worked perfectly when it was plugged in but wont work on my 19" LCD monitor :confused: i have a nvidia geforce 6200xfx grafix card and amd x64 dual core proseeser and running ubuntu 7.10, the desktop effects worked perfectly in 7.04 :confused:
please reply soon and help me out with this problem thanks :KS

---

### Post by LyricalK on 2007-11-18
anyone?

---

### Post by Forlong on 2007-11-19
Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's CODE tag please (# button)

---

### Post by LyricalK on 2007-11-19
thats what i got n fnx first post :)
```
dru@dru-desktop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
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
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1440x900"
        Horizsync       31.5-56.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44A [GeForce 6200]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1440    900
                Modes           "1440x900@60"   "1280x800@60"   "1280x720@60"  "1280x768@60"    "800x600@60"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection
Section "device" #           
        Identifier      "device1"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" #           
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" #           
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
dru@dru-desktop:~$ 

```

---

### Post by Forlong on 2007-11-19
Do this:
```
sudo dpkg-reconfigure xserver-xorg
```
then this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Then restart X and try again.

---

### Post by LyricalK on 2007-11-19
i did and the resolution changed again too somethin too high, i pluged it into ma tv agen  n it works proper but when i plug it into my monitor it says its too high and i cant log in now as soon as i log in it takes ma back to the logon screen so i am in failsafe gnome what can i do thanks

---

### Post by LyricalK on 2007-11-20
i fixed the resolution problem but i still cant enable desktop effect :S

---

