---
title: "Change primary monitor?"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by Skeorx13 on 2007-06-16
I have a problem with my dual monitor setup. I have two flat screen monitors, one 19" and one 15" to the right. I have set up twinview to make one desktop out of it. However, the small screen is set to my primary monitor. I would like to be able to have my 19" monitor as the primary screen. This has been causing problems when viewing videos as the fullscreen mode always sends the full screen to my small monitor, not the large one where I would like it to be. I figured I could just change the ordering of the monitors in my xorg.conf file, but the horizontal refresh and vsync rates aren't identical and I don't want to fry my monitors. I am also incapable of switching the plug positions in my graphics card because I have a watercooling radiator in the way and my small monitor has a CRT to DVI adapter attached to it. I tried messing with nvidia-settings but I can't figure out how to swap the monitor priority. This is also been annoying because my login screen goes to the small screen instead of the large one as well. Does anyone have some insight to alleviate my annoyances?

My xorg.conf for reference:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen [0]" 0 0
    Screen      1  "Default Screen [1]" RightOf "Default Screen [0]"
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
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option	   "ButtonMapping" "1 2 3 6 7"
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
    Identifier     "Radius [0]"
    Option         "DPMS"
    HorizSync	   30-60
    VertRefresh	   55-75
EndSection

Section "Monitor"
    Identifier     "ViewEra [1]"
    Option         "DPMS"
    HorizSync	   30-81
    VertRefresh	   55-75
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   1
EndSection

Section "Screen"
    Identifier     "Default Screen [0]"
    Device         "NVIDIA Corporation NVIDIA Default Card0"
    Monitor        "Radius [0]"
    DefaultDepth    24
    Option         "Twinview" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "55-75"
    Option         "NvAGP" "1"
    Option         "HWCursor" "0"
    Option         "SWCursor" "1"
    Option         "NoLogo" "False"
    Option         "RenderAccel" "True"
    Option         "MetaModes" "1024x768,1280x1024; 1024x768,1024x768; 800x600,800x600; 640x480,640x480; null,1280x1024; null,1024x768; null,800x600; null,640x480; 1024x768,null; 800x600,null; 640x480,null"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen [1]"
    Device         "NVIDIA Corporation NVIDIA Default Card1"
    Monitor        "ViewEra [1]"
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

---

### Post by Hobo Joe on 2007-10-22
I know I'm bumping a super old thread, but I have this same problem, and I'd really like a fix. It's one of the few things holding me back from switching completely to Linux.

---

### Post by WiFi Ed on 2007-10-23
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "true"
    Option         "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option         "UseDisplayDevice" "DFP, CRT"
    Option         "TwinViewOrientation" "DFP LeftOf CRT"
```

That's how I made mine work. I have a LCD (aka "DFP") and a regular monitor (aka "CRT"). I can't guarantee it will work for you guys, but it might be a good place to start. You might need to change "DFP" to "DFP-0" and "DFP-1 for your respective monitors, I think I saw an error message in a log file once saying that Xorg was changing mine to add the -0 and -1 on the fly as it booted up, but I'm not completely sure about that.

Good luck!

---

