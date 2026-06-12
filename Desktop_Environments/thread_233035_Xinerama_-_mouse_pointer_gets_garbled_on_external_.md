---
title: "Xinerama - mouse pointer gets garbled on external screen"
date: 2006-08-09
forum: Desktop Environments
---

### Post by pjvaanan on 2006-08-09
Hi,

have I missed some option in xorg.conf?
Mouse pointer is working on my laptops screen
but when moved to the external xinerama screen
it gets garbled (about 100x100 pixel box
with white/black/grey lines.)

dev: ATI X1600 mobility
xinerama1: A6JA 1280x800
xinerama2: VP201b 1600x1200

It happends also with
Acer 8204Wlmi with 19" external screen (1280x1024)

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "screenlcd" 0 0
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
        Option      "XkbLayout" "fi"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "lcd"
        HorizSync    28.0 - 64.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "external"
        HorizSync    30.0 - 92.0
        VertRefresh  50.0 - 85.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "atix1600"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option      "MonitorLayout" "CRT,LFP"
        Screen      0
EndSection

Section "Device"
        Identifier  "atix1600external"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option      "MonitorLayout" "CRT,LFP"
        Screen      1
EndSection

Section "Screen"
        Identifier "screenlcd"
        Device     "atix1600"
        Monitor    "lcd"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "screenexternal"
        Device     "atix1600external"
        Monitor    "external"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes     "1600x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Extended Layout"
        Screen          0 "screenlcd" 0 0
        Screen          1 "screenexternal" RightOf "screenlcd"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        Option          "Xinerama" "true"
        Option          "Clone" "off"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
#        Option  "AllowMouseOpenFail" "true"
#       Option  "DefaultServerLayout" "Default Layout"
        Option  "DefaultServerLayout" "Extended Layout"
EndSection
```

---

### Post by marshallfox on 2006-10-06
Hi,

I am having a similar problem... did you find any workaround?

marshall

---

### Post by arvelius on 2006-10-23
Same to me. Has anyone sent a bugreport, either to xinerama or ubuntu?

/Johan

---

### Post by gts on 2006-10-24
Same to me...

---

### Post by gts on 2006-10-24
My configuration is:
Radeon 9800 pro
Kubuntu Edgy RC (I have this trouble since I upgraded to Edgy)

---

### Post by pjvaanan on 2006-10-26
There's a thread with a solution which worked for me!
[here]("http://www.ubuntuforums.org/showthread.php?p=1589155")

---

