---
title: "Multi Monitor with an AGP and a PCI Nvidia card"
date: 2006-08-08
forum: Desktop Environments
---

### Post by computergroove on 2006-08-08
I hate to have to resort to this but I have spent days trying this and I have run out of ideas. I have Dapper installed and I have a TNT2 PCI Video card and a Geforce 4 Ti 4200 Agp card in my machine. I booted into live wiht each card seperately and recorded the PCI location and then installed both cards and manually edited the xorg.conf file. I have tried several configurations but with no luck. Here is my xorg.conf file right now:

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
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom"# Change to /dev/input/event for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to /dev/input/event for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to /dev/input/event for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Driver "nvidia"
BusID "AGP:1:0:0"
Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
Driver "nv"
BusID "PCI:2:12:0"
Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
Identifier "DELL E156FP" #flat monitor
Option "DPMS"
EndSection

Section "Monitor"
Identifier "DELL P780" #CRT DELL Monitor
Option "DPMS"
EndSection

# Section "Monitor"
# Identifier "Generic Monitor"
# Option "DPMS"
# HorizSync 28-51
# VertRefresh 43-60
# EndSection

Section "Screen"
Identifier "Ti_4200"
Device "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Monitor	"DELL P780"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "TNT2"
Device "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
Monitor	"DELL E156FP"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Ti_4200"
# Screen "TNT2" Above "Ti_4200"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection	

Section "ServerFlags"
Option "DefaultServerLayout" "Default Layout"
EndSection


I cant get the second monitor/video card to initialize at all (TNT2 / Dell Lcd DELL E156FP). Can anyone see anything out of place or offer some suggestions?

---

