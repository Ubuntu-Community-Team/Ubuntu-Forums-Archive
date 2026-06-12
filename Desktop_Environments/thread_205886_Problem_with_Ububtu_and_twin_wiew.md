---
title: "Problem with Ububtu and twin wiew"
date: 2006-06-29
forum: Desktop Environments
---

### Post by ExtruderNOR on 2006-06-29
I am an linux n00b .

I have bought a laptop based on MSI 1032 barebone - [http://www.msicomputer.com/NB/produc...?model=MS-1032](http://www.msicomputer.com/NB/produc...?model=MS-1032) .

I have installed Ubuntu 6.06 . I have followed a how-to and installed the latest Nvidia driver .

I am connecting a old Hansol CRT to the laptop . After a lot of work I got twin wiew to work , but the CRT is automaticly choosed as the primary screen . Is there anyway I can deside what screen is the primary ?

The CRT screen is 4:3 and the laptop screen is widescreen .
In screensolution under "System" is says 2560x1024 at 50 Hz - so watching the CRT for long periodes of time makes my head hurt .
Is there any way I can set up diffrent screensolutions for eacth monitor ? the nvidia controll panel detect the two monitors but I can`t set resolutions og refresh rates there ?


My xorg.config file - a little messy but ...


Section "ServerLayout"
Identifier "TwinView Configuration"
Screen "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
Option "Xinerama" "Off"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
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
Option "XkbModel" "pc105"
Option "XkbLayout" "no"
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
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28.0 - 64.0
VertRefresh 43.0 - 60.0
Option "DPMS"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce Go 6600]"
Driver "nvidia"
Option "TwinView" "true"
Option "TwinViewOrioentation" "Rightof"
Option "metamodes" "1280/800,1280/800 ; 1024/768,1024/768 ; 1280/800,NULL ; 1024/768,NULL"
Option "Coolbits" "1"
Option "SecondMonitorHorizSync" "UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs"
Option "Monitor Layout" "DFP, CRT"
Option "Clone" "false"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce Go 6600]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Viewport 0 0
Depth 1
Modes "1280x1024" "1280x800" "1024/768"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1280x800" "1024/768"
EndSubSection
EndSection

I am grateful for any advice

---

### Post by ExtruderNOR on 2006-07-10
Bump . 

Can anyone healp me set ut 2 monitors with different resolutions ? 

In Windows this is so easy , must I go back to that ?

---

### Post by BungaMan on 2006-07-10
Does this help? [http://www.ubuntuforums.org/showthread.php?t=23647](http://www.ubuntuforums.org/showthread.php?t=23647)

I've never tested dual monitor on ubuntu myself.. maybe I should :)

---

### Post by javierfh on 2006-07-10
Hello Extruder,

i dont know much about but there is this excellent howto.
As i said i dont know much about, but in a way i managed to make it working. I have also similar problems with refresh rates, but still works in a way.
If you want to read about it check that thread

[http://ubuntuforums.org/showthread.php?t=85769&highlight=twinview](http://ubuntuforums.org/showthread.php?t=85769&highlight=twinview)


Hope that helps ,

Javi

---

