---
title: "compiz crash after logout-login"
date: 2006-12-28
forum: Desktop Environments
---

### Post by smeto on 2006-12-28
i install compiz-freedesktop 0.3.4 latest packages.
when enable gl desktop (system,preferences,gl desktop), everything works great.
but when i log out and log in, i see black desktop without panels.

where’s problem?

i use ubuntu edgy, mesa drivers from original repositories, GMA900 graphic card,enabled compiz with metacity support (gtk-window-decorator).

my xorg.conf

```

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
Load "bitmap"
Load "ddc"
# Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
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
Option "Buttons" "6 7 8 9"
Option "ButtonMapping" "1 2 3 6 7"
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
Identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 65536
#Videoram 131072
Option "XAANoOffscreenPixmaps"
Option "VBERestore" "true"
Option "DRI" "true"
EndSection

Section "Monitor"
Identifier "Benq FP931"
Option "DPMS"
HorizSync 30-82
VertRefresh 50-77
# DisplaySize 270 203 # 1024x768 96dpi
# DisplaySize 338 254 # 1280x960 96dpi
DisplaySize 338 270 # 1280x1024 96dpi
# DisplaySize 370 277 # 1400x1050 96dpi
# DisplaySize 423 370 # 1600x1400 96dpi
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
Monitor "Benq FP931"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection 

```

---

