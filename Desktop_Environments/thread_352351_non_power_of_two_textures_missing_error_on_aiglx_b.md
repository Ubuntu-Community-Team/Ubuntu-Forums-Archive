---
title: "non power of two textures missing error on aiglx beryl"
date: 2007-02-03
forum: Desktop Environments
---

### Post by weekendli on 2007-02-03
After I start my beryl aiglx, I got following error and gnome frozen. Basically the error msg is "non power of two textures missing"

The situation here is my video card is ati radeon 7500 mobility, and the xorg driver currently using is "ati".

Do you know what goes wrong in my configuration? Or any chance I can get beryl working on my laptop.

Thank you.

************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : failed

Support for non power of two textures missing

---------------------------------------------------------------------------------------------------------
#############################################
# xorg.conf
#############################################
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "dbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
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
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by sloggerkhan on 2007-02-03
If your cube has backround images that aren't in the correct aspect ration it might not like it.
(power of 2s in dimmensions of 2:1 or 1:1 I think.)

---

