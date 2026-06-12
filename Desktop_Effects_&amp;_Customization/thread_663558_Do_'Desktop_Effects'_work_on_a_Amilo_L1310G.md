---
title: "Do 'Desktop Effects' work on a Amilo L1310G"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by Muflon on 2008-01-10
Hi

I have installed Ubuntu (7.10) on a Fujitsu Amilo L1310G.  I worked through several issues including Wireless and screen resolution but after using the following links I Have been unable to get the 'Desktop Effects' working.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually)
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
[http://ubuntuforums.org/showthread.php?t=450748](http://ubuntuforums.org/showthread.php?t=450748)

Before I give up, can anyone confirm that it is actually possible to get 'Desktop Effects' working on a L1310G.

Thanks

Muflon

---

### Post by codesplice on 2008-01-10
Are you getting any sort of error messages when you try to launch Desktop Effects?

Can you post the output of trying to launch compiz from a terminal?  Also, what do you get when you
```
$ glxinfo | grep direct
```?

And the contents of your /etc/X11/xorg.conf file?

---

### Post by Muflon on 2008-01-10
Hi Codesplice

compiz reports

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5a62 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

glxinfo | grep direct

```
direct rendering: Yes

```

/etc/X11/xorg.conf

```
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "MinSpeed" "0.45"
        Option          "MaxSpeed" "0.75"
        Option          "AccelFactor" "0.020"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RC410 [Radeon Xpress 200M]"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RC410 [Radeon Xpress 200M]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

#Section "Extensions"
#       Option          "Composite"     "0"
#EndSection

```

Thanks

Muflon

---

### Post by codesplice on 2008-01-10
Thanks for posting those.  I see two issues:  

1) make sure you have the xserver-xgl package installed.  Compiz reporting that XGL is not found indicates that it's probably not installed.

2)  At the bottom of your xorg.conf file, uncomment the last section, and change
```
Option        "Composite"       "0"
```
 
to

```
Option        "Composite"       "Enable"
```

Lemme know if that does/doesn't work for you :)

---

### Post by Muflon on 2008-01-10
Hi 

I made the suggested changes, I still can't enable the Desktop Effects and the screen flashes when redrawing a window.

compiz also reports

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

Thanks

Mufon

---

### Post by Forlong on 2008-01-10
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by Muflon on 2008-01-11
After checking, I am already running the latest version of xserver-xgl

Muflon

---

### Post by Muflon on 2008-04-03
I now have Compiz running but it impacts the speed of scrolling in Firefox so I have turned it off. :(

---

