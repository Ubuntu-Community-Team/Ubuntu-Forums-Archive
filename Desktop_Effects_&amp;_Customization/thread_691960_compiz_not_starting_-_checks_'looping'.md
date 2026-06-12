---
title: "compiz not starting - checks 'looping'"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by Fluffylob on 2008-02-09
Hello,

I'm trying to get compiz running without XGL on my ATI X1600 Mobility as XGL interferes with the powersaving options of the ATI.  I'm using the latest binary ATI driver from ati.com.

My problem is that when trying to start compiz with compiz --replace, various checks are performed, and the script tries to start gtk-window-decorator, but nothing happens and it immediately restarts the same checks, getting itself in a never ending loop.  If I run gtk-window-decorator --replace directly from terminal, nothing appears to happen.

Thank you for any help anyone can offer - details are below...
Chris

FGLRXINFO output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7276 Release
```

Output when running compiz --repalce
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
**Starting gtk-window-decorator**
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
**Starting gtk-window-decorator**
...repeats until cancelled...
```

xorg.conf
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "XAANoOffscreenPixmaps" "True"
        Option      "TexturedVideo" "True"
        Option      "TexturedVideoSync" "True"
        Option      "Textured2D" "True"
        Option      "TexturedXrender" "True"
        Option      "UseFastTLS" "2"
        Option      "BackingStore" "True"
        Option      "MaxGARTSize" "128"
        Option      "VideoOverlay" "on"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "RENDER" "Enable"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"
Option "XVideo" "Enable"
EndSection
```

---

### Post by hoangminh88 on 2008-02-19
Me too

---

### Post by Fluffylob on 2008-02-19
FWIW, I eventually gave up troubleshooting and formatted and re-installed Gutsy.

On a fresh install with the latest ATI binary, compiz runs fine without XGL.  I guess one of the various drivers / settings I messed with first time round must have been causing issues.

Sorry I can't be more specific.

Cheers,
Chris

---

