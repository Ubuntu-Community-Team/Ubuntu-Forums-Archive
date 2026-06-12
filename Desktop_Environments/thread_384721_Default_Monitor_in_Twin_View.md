---
title: "Default Monitor in Twin View"
date: 2007-03-14
forum: Desktop Environments
---

### Post by ai3x on 2007-03-14
Hi,

I'm new to ubuntu and trying to make a go out of it. After much googling and playing I've finally managed to get nvidia twinview up and running, I just have one problem. I have two screens, one of which is a Samsung TV and the other a Xerox 19" monitor, now for some reason twinview keeps making the samsung the default screen. That is all the popups i get when i start an application start on the samsung not the xerox and since it is a TV this really isn't what I want! Any ideas on how to fix this?

Here is a copy of my xorg.conf file:


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Xerox"
    HorizSync       28.0 - 79.0
    VertRefresh     43.0 - 80.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
	Option "TwinView" "true"
	Option "RenderAccel" "true"
	Option "UseEdidFreqs" "true"
	Option "ConnectedMonitor" "DFP-0, CRT-1"
	Option "MetaModes" "1280x1024, 1360x768;"
	Option "TwinViewOrientation" "RightOf"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Xerox"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection



thanks in advance for any help you can give, this really is a deal breaker to ubuntu at the moment  :S

Alex

---

### Post by ai3x on 2007-03-15
Anybody?

---

### Post by Snyper64 on 2007-03-18
Try changing this:

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "TwinView" "true"
Option "RenderAccel" "true"
Option "UseEdidFreqs" "true"
Option "ConnectedMonitor" "DFP-0, CRT-1"
Option "MetaModes" "1280x1024, 1360x768;"
Option "TwinViewOrientation" "RightOf"
EndSection

To this:

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "TwinView" "true"
Option "RenderAccel" "true"
Option "UseEdidFreqs" "true"
Option "ConnectedMonitor" "DFP-0, CRT-1"
Option "MetaModes" "1280x1024, 1360x768;"
Option "TwinViewOrientation" "RightOf" [COLOR="Red"]"Default Screen"[/COLOR]
EndSection

---

