---
title: "beryl causes white screen"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by dazman19 on 2007-08-11
Hi,

I (think) I have almost got beryl working, I can run the manager, emerald theme manager and make it a selectable session at the GDM startup page. 

But when I start it, the screen goes white, The cube functionality works, i can spin it around and it goes pretty fast but all the sides of the cube are white there is no icons etc except the top and bottom of the cube that have the beryl diamond, I have been trying for ages to get this working and I feel i am so close..... 

And the only way for me to get back is to restart x (the GDM) the old CTRL + ALT + Backspace.

I am running dapper drake user 6.06.1 on a notebook with dual core pentium 1.86Ghz (yonah) with an ATI Mobility Radeon x1300 64MB Gfx card. Screen is 1280x800 wide. And the cube seems to fit perfectly in the widescreen.

I have read heaps of threads on this and have tried a few things like changing the composite from "0" to "Enabled" but it doesnt work and runs really slow when I do that.

Any1 know what might be wrong?

Heres some more info:

daz@daz-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300 Generic
OpenGL version string: 2.0.5814 (8.25.18)

daz@daz-laptop:~$ glxinfo | grep direct
direct rendering: Yes

daz@daz-laptop:~$ cat /etc/X11/xorg.conf

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 64.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "radeon"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "EXA"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection


Thanks 
Daz

---

