---
title: "kubuntu | dual X screens | desktop shortcuts behaviour"
date: 2007-05-01
forum: Desktop Environments
---

### Post by tomele on 2007-05-01
Hi everybody,

I am using dual X screens, one of them being bound to the TV output of my nvidia video card. This setup works smoothly and allows me to run video fullscreen on my TV while still being able to work on my LCD screen (eg. 'DISPLAY=":0.1" vlc --fullscreen video.avi').

The problem is I can't get the keyboard shortcuts to work properly (the ones you configure via KDE Menu Editor):  when the mouse cursor is on my main LCD screen, pressing shortcut keys just do nothing; whereas when the cursor is on the TV screen, the shortcuts do launch their apps on TV screen, which is rather useless. 

I am dual booting kubuntu Edgy and Feisty with same exact behaviour; I used ubuntu before (Dapper and Edgy) and had not the same problem with gnome.

I am copying my xorg.conf below, any help would be greatly appreciated !


```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0 "Screen[0]"
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
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
    Option         "XkbLayout" "fr"
    Option         "XkbVariant" "latin9"
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

Section "Monitor"
    Identifier     "Monitor[0]" #LCD
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor[1]" #TV
    HorizSync       30 - 50
    VertRefresh     50.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    Screen 0
EndSection

Section "Device"
    Identifier     "Device[1]"
    Driver         "nvidia"
    Screen 1
    Option          "TVOutFormat" "SVIDEO"
    Option          "TVStandard" "PAL-G"
    Option          "ConnectedMonitor" "Monitor[1]" 
    BusID           "PCI:5:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
  	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
      	SubSection "Display" 
              Depth 24 
              Modes "720x576_50" 
      	EndSubSection    
EndSection

```

---

### Post by tomele on 2007-05-01
Some hint, anyone ?

---

### Post by tomele on 2007-05-02
Last attempt at moving up this thread, in hope for some X.org guru to come by...

---

