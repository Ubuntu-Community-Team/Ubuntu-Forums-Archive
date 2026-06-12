---
title: "1920x1200 resolution on Latitude D820"
date: 2007-06-21
forum: Dell  Ubuntu Support
---

### Post by ketchera on 2007-06-21
Hello,

I'm trying to set the screen resolution at 1920X1200 on my laptop Dell Latitude D820.
I have Ubuntu 7.04.
I've tryed these :
* [http://lamouroux.net/blog/?p=23](http://lamouroux.net/blog/?p=23)
* [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

But no changes....
lspci output :

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
-------------------------------------------------
 
=====================================

xorg.conf 

----------------------------------


Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        #Driver         "nvidia"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

--------------------------------------------------------

Thanks,
Iuli.

---

### Post by koshatnik on 2007-06-21
For work, I use a Dell latitude d800 and have no problems with the max resolution. I'll have a fish about see if I can come up with a solution. Can you post your entire xorg.conf file on here?

---

### Post by ketchera on 2007-06-21
xorg.conf :

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        #Driver         "nvidia"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200"
         Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200"
                #Modes          "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by calvinator on 2007-06-21
Hi! 

I recently had the problem that the reference to physical adress of the graphic card in xorg.conf was altered during an update, which caused the system to crash. Maybe your problem is similar...

If you are dual-booting start windows hardware manager and check the adress of your card (in my case it was 1:0:0), and then control if it matches with the one in your xorg.conf file.
I hope this can help you...

---

