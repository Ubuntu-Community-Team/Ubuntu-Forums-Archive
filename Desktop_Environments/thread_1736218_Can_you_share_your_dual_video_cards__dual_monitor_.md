---
title: "Can you share your dual video cards / dual monitor xorg.conf?"
date: 2011-04-22
forum: Desktop Environments
---

### Post by chairman_faust on 2011-04-22
I'm not new to linux, but new to using it on a desktop, I can't for the life of me seem to get my two video cards with monitors to work, trying both 10.10 and 11.04, the monitor tool does not recognize my second monitor.. On 11.04, unity seems to work on 1 monitor, I dont really care if I get unity working or not but i would like to have both monitors working as 1 shared desktop (if possible)... the xorg.conf posted below worked for 1 reboot but crashed all unity apps and defaulted to standard gnome, also i could move the mouse between monitors but not drag apps... here is some info:
 
lspci -v:
```

00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 2808
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at f0400000 (32-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1200 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Kernel driver in use: i915
        Kernel modules: i915

```
 
```

07:04.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1) (prog-if 00 [VGA controller])
        Subsystem: Jaton Corp Device 0000
        Flags: 66MHz, medium devsel, IRQ 20
        Memory at f1000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
        [virtual] Expansion ROM at d7e00000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Kernel modules: nouveau, nvidiafb

```
 
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen         "Screen0"
        Screen         "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
# Section "ServerFlags"
#       Option "Xinerama" "true"
# EndSection
# Section "DRI"
#       Mode    0666
# EndSection
Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection
Section "Module"
        Load  "dri2"
        Load  "record"
        Load  "extmod"
        Load  "dri"
        Load  "glx"
        Load  "dbe"
EndSection
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"               # [<str>]
        #Option     "DRI"                       # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "VideoKey"                  # <i>
        #Option     "FallbackDebug"             # [<bool>]
        #Option     "Tiling"                    # [<bool>]
        #Option     "Shadow"                    # [<bool>]
        #Option     "SwapbuffersWait"           # [<bool>]
        #Option     "XvMC"                      # [<bool>]
        #Option     "XvPreferOverlay"           # [<bool>]
        #Option     "DebugFlushBatches"         # [<bool>]
        #Option     "DebugFlushCaches"          # [<bool>]
        #Option     "DebugWait"                 # [<bool>]
        #Option     "HotPlug"                   # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "WrappedFB"                 # [<bool>]
        #Option     "GLXVBlank"                 # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        Identifier  "Card1"
        Driver      "nouveau"
        BusID       "PCI:7:4:0"
EndSection
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes "1280x1024"
        EndSubSection
EndSection
Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes "1280x1024"
        EndSubSection
EndSection

```

---

### Post by Krytarik on 2011-04-22
The reason why you were not able to move windows between the monitors, is that they were set up as separate xscreens, not as "Xinerama". However, I guess if you do so you will lose the ability to run Compiz (desktop effects). I modified your xorg.conf to enable Xinerama, and evicted it of the imo unnecessary parts:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen         "Screen0"
        Screen         "Screen1" RightOf "Screen0"
        Option         "Xinerama"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Device"
        Identifier  "Card1"
        Driver      "nouveau"
        BusID       "PCI:7:4:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes "1280x1024"
        EndSubSection
EndSection
```Another option, if those xorg.conf still causes your xserver to crash, is to add the specs of each monitor to it, like this, for example (these are mine):
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-4401"
[B]    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
[/B]    Option         "DPMS"
EndSection
```To get them you can
- run "hwinfo --monitor" (package "hwinfo" needed)
- run "xvidinfo" and press "Cancel"
- check the monitor's manual, do a web search
- also see here: [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

Some of the tools may report incorrect values!

Good luck!

---

