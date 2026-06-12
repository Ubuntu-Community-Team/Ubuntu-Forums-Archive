---
title: "Video Driver Installation on a Dell Latitude D610, HELP!!"
date: 2006-03-08
forum: Desktop Environments
---

### Post by jgservices on 2006-03-08
I have a Dell Latitude D610 laptop, and it works great on Ubuntu! Everything works great when the laptop is by itself, but the screen is small and is poor quality. I have a docking station which this laptop goes into, and I'd like to use it. I have the screen closed and it's docked in the station, and I have another LCD connected to the VGA port on the docking station, on boot up with this configuration the LCD is set as the primary display, which is what I want to work. However, when i do this, Ubuntu ALWAYS boots up in 640X480 and I can't change the resolution!! This obviously is a video driver problem, but I have no idea how to install it. I downloaded the driver for an Intel video graphics chip 915GM or something, it's in the Dell specs, but I cannot for the life of me install it. It has makefile and some other .sh files, but they will not do anything. I love Ubuntu and I use Crossover Office a lot and would really like to get my resolution up on my LCD!!! Can ANYONE help me please and thanks??

---

### Post by SysKoll on 2007-02-07
Did you solve your problem?

For the Dell 610, there are apparently two kind of models. Some have an ATI graphics subsystem, some have an Intel 915 chipset.

For the 915 graphics, here are instructions: [http://www.kcore.org/?menumain=4&menusub=2](http://www.kcore.org/?menumain=4&menusub=2)

For the ATI graphics, you need to install the ATI driver (fglrx) and then the /etc/X11/xorg.conf file is:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

#       FontPath        "/usr/share/X11/fonts/cyrillic"
        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
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
        Option      "XkbModel" "pc105"
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
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
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

```

---

