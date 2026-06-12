---
title: "Screen resloution issue"
date: 2007-12-22
forum: Desktop Environments
---

### Post by maxim1 on 2007-12-22
Can any one help, I seem to be having problems with screen resolution, it was working fine until I tried dual monitors. I had an issue with different resolutions on each monitor which i managed to sort out. I am just going to use laptop screen as its better than my LCD, anyway since fooling about with the x11 conf file my laptop will not remember my desired screen resolution of 1680x1050, its always set at 1280x768. I can go and change it to 1680x1050 which is a problem as beryl auto loads on startup and will not allow me to change the resolution correctly.

Please any suggestions to fix the issue of remembering screen resolution will be appreciated.



Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
Inputdevice "stylus" "SendCoreEvents"
Inputdevice "cursor" "SendCoreEvents"
Inputdevice "eraser" "SendCoreEvents"
Inputdevice "Synaptics Touchpad"
EndSection

Section "Files"

# path to defoma fonts
Fontpath "/usr/share/X11/fonts/misc"
Fontpath "/usr/share/X11/fonts/cyrillic"
Fontpath "/usr/share/X11/fonts/100dpi/:unscaled"
Fontpath "/usr/share/X11/fonts/75dpi/:unscaled"
Fontpath "/usr/share/X11/fonts/Type1"
Fontpath "/usr/share/X11/fonts/100dpi"
Fontpath "/usr/share/X11/fonts/75dpi"
Fontpath "/usr/share/fonts/X11/misc"
Fontpath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "int10"
Load "type1"
Load "vbe"
Load "glx"
Load "v4l"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom"# Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom"# Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom"# Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1680x1050"
Horizsync 31.5-65.5
Vertrefresh 56.0 - 65.0
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
modeline "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
modeline "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
modeline "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
modeline "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
Gamma 1.0
EndSection

Section "Device"
Identifier "Generic Video Card"
Boardname "nv"
Busid "PCI:1:0:0"
Driver "nvidia"
Screen 0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
Defaultdepth 24

Option "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
Virtual 1680 1050
Modes "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
EndSubSection
EndSection

Section "device" #
Identifier "device1"
Boardname "nv"
Busid "PCI:1:0:0"
Driver "nvidia"
Screen 1
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
SubSection "Display"
Depth 24
Modes "640x480@60"
EndSubSection
EndSection
Section "monitor" #
Identifier "monitor1"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by maxim1 on 2007-12-23
OK sorted it, any one wishing to know how set the screen resolution in screen resolution in system preferences as well as in screens and graphics

---

