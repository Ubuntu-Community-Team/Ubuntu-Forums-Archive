---
title: "Cant get true color in xorg"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Clanman on 2006-08-30
Hello
I have tried setting depth to 16 and 24 but its no difference
The modlines are alculated from  [http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php)
I have a samsung syncmaster 205BW TFT monitor that supports 1680x1050at 60Hz

the screen is using the right resolution but the colors are bad. I get large areas with the same color on photos (moare)

here is my xorg.conf

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
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "sv"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        UseModes        "16:9"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section  "Modes"
        Identifier      "16:9"
        Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection



Please help me

---

### Post by Clanman on 2006-08-30
I noticed i posted an xorg.conf with 
Depth set to 16
se below

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NVIDIA Default Card"
Monitor "SyncMaster"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

However it doesnt matter if I change this to 24. Xorg still shows only 16 bit

 cat /var/log/Xorg.0.log

says it is in 24 bit 
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32

Please help me

---

### Post by robert114 on 2006-10-26
Does it look like this?

[http://ubuntuforums.org/attachment.p...1&d=1161854767](http://ubuntuforums.org/attachment.p...1&d=1161854767)

---

