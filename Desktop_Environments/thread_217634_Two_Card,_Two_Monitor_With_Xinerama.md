---
title: "Two Card, Two Monitor With Xinerama"
date: 2006-07-17
forum: Desktop Environments
---

### Post by thoolihan on 2006-07-17
I have a problem trying to set up two monitors in X. It is similar to the following post, but this was never resolved for the user.

[http://www.ubuntuforums.org/showthread.php?t=78095&highlight=Xinerama+deleted+matching+config](http://www.ubuntuforums.org/showthread.php?t=78095&highlight=Xinerama+deleted+matching+config)

I have Xinerama set up similar to the guides I have found on this and X starts, but only on the AGP monitor.  This is true, even if I set the pci card to be primary in the bios.  In that situation,  the boot output and bios splash is on the pci screen, but X starts on the AGP screen.  I have tried this with two pci screens but get the same results.

I have two cards, one AGP and one PCI as lspci -X shows:
PCI:0:9:0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 4 / Voodoo 5
PCI:1:0:0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500]

The errors I get in /var/log/Xorg.0.log are:

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
[B](WW) TDFX: No matching Device section for instance (BusID PCI:0:9:0) found
(EE) Screen 1 deleted because of no matching config section.[/B]
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.

I have posted my xorg.conf below.  Any assistance is greatly appreciated.  
Thanks!
-Tim

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "ServerFlags"
    Option "xinerama" "true"
    Option "DefaultServerLayout" "Default Layout"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
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
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
    Identifier  "3DFX"
    Driver      "tdfx"
        BusID           "PCI:0:9:0"
    Screen 1
EndSection

Section "Device"
        Identifier      "GEFORCE"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
    Option      "RenderAccel"   "true"
    Option      "AllowGLXWithComposite" "true"
    Option      "NvAGP" "3"
    Screen  0
EndSection

Section "Monitor"
        Identifier      "Monitor1"
        Option          "DPMS"
        HorizSync       28-80
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "Monitor2"
        Option          "DPMS"
        HorizSync       28-80
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "GEFORCE"
        Monitor         "Monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                #Modes          "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device      "3DFX"
    Monitor     "Monitor2"
    DefaultDepth    24
    SubSection  "Display"
        Depth   24
        Modes   "1280x1024" "1024x768"
    EndSubSection
    SubSection  "Display"
        Depth   16
        Modes   "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen1"
    Screen      "Screen2" LeftOf "Screen1"
    Option      "Xinerama" "on"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by thoolihan on 2006-08-06
Turns out the Screen 0, Screen 1 lines needed to be deleted from the device sections.

---

