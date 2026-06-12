---
title: "Odd XGL experience"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-05-02
I currently have a separate login session for XGL that i set up in the process of getting fglrx ATI drivers to accelerate my desktop. I noticed some odd things about its behavior:


List of negative observations:
-simple gnome effects, such as the "growing square" that eminates from launchers in the panel, run very slow!
- loading a page that has Flash takes 60% of my cpu
- watching large flash/FLV videos, such as a fullscreen youtube video, is choppy / lwo frame rate.
- 3D games (such as Second Life) have extremely poor framerate

Are these symptoms of a mal-configured setting in some obscure text file somewhere? Or is this a simple fact of life that goes with this set up?

I'd like to point out that Beryl runs beautifully while in the XGL session, and I can avoid all of these problems by simply logging into the non-XGL gnome or KDE session (and loose the accelerated desktop effects).

---

### Post by superyounan1 on 2007-05-02
bump (sorry)

---

### Post by superyounan1 on 2007-05-02
I figured out that Direct Rendering (DRI) isnt running in my XGL session:

```

glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
direct rendering: No

```

I'll be digging around to see if I can enable it with my XGL+fglrx configuration. This is my xorg.conf if it is usefull for anyone that knows how to fix it:

```
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
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Emulate3Buttons" "false"
        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"# Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"# Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"# Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "SyncMaster"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver      "fglrx"
        Option      "TVOverscan" "on"
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Monitor    "SyncMaster"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

---

