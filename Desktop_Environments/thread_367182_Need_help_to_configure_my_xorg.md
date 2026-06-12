---
title: "Need help to configure my xorg"
date: 2007-02-21
forum: Desktop Environments
---

### Post by bitou on 2007-02-21
I want to plung in laptop anoter screen via the my VGA output. I can't manage it with Beryl.
This my xorg.conf
It worked before Beryl :(

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
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

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "Intel-LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option     "GARTSize"     "64"
        Option          "VBERestore" "true"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
       Identifier      "Intel-external"
        Driver          "i810"
        #Driver         "vesa"
        BusID           "PCI:0:2:0"
        #VideoRam        16384
        Option          "Display"       "CRT"
        Option          "MonitorLayout" "CRT,LFP" # put crt on pipe A
        Screen          1
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
        HorizSync       30.0-71.0
        VertRefresh     50-160
EndSection


Section "Monitor"
        Identifier      "Philips 107S"
        VendorName      "Philips"
        ModelName       "107S"
        Option          "DPMS"
        HorizSync       30.0-70.0
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Local LCD"
        Device          "Intel-LCD"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                # use "1400x1050" or "1280x800" for a widescreen
                Modes           "1280x800" "1280x1024" "1024x768" "800x600"
                # use standard resolutions for non-widescreens
                #Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Monitor"
        Device          "Intel-external"
        Monitor         "Philips 107S"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
               Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection



Section "ServerLayout"
        Identifier "Dual Head Layout"
        Screen 0        "Local LCD"     0 0
        Screen 1        "External Monitor" RightOf "Local LCD"
        InputDevice     "Generic Keyboard"
        Option "AIGLX" "true"
EndSection

Section "ServerFlags"
        Option "Xinerama" "true"
EndSection

Section "DRI"
        Mode    0666
EndSection
```
 
Someone can help me or provide me his xorg (for Edgy, intel, beryl, VGA-OUT,  Xinerama(not mandatory ) ).

---

