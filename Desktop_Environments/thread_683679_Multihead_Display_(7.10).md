---
title: "Multihead Display (7.10)"
date: 2008-01-31
forum: Desktop Environments
---

### Post by Armadillos on 2008-01-31
I have the following setup:

Dell Latitude D830 Laptop with nVidia Quadro NVS 140M card
Ubuntu 7.10 64bit

I have a port replicator that I put my laptop.  The port replicator has two video outputs, one VGA and one DVI.  I have successfully been able to connect a Dell widescreen monitor to the DVI port and I have a working 'stretched' desktop between the laptop screen and the Dell screen.

However I am curious as to know whether I can connect yet another monitor to the now spare VGA socket.  I have tried several xorg.conf variations and have not got it to work.
I have tried both Xinerama and TwinView, but they do not seem to work.

The interesting thing is that the graphics card does seem to see all the monitors as shown in this excerpt from my Xorg.0.log file:
```

(--) NVIDIA(0): Connected display device(s) on Quadro NVS 140M at PCI:1:0:0:
(--) NVIDIA(0):     HP L1740 (CRT-0)
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     DELL 2007FP (DFP-1)
(--) NVIDIA(0): HP L1740 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): DELL 2007FP (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 2007FP (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
```

However I do not seem to be able to get them all working at the same time.

Here is my Xorg.conf file:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP L1740"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard0"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I know at the moment I am using TwinView - I am not even sure that this can do what I want.

I have used the nvidia-settings program, but everytime I try and save the file I get the following error

• MetaMode 1 of Screen 0 has more than two active display devices.


I am not sure if this is at all possible, but I am sure that the laptop is seeing all the monitors so both graphics ports are enabled.

Does anyone have any idea on how to do this?

Thanks

---

### Post by chewearn on 2008-02-01
I don't think it's possible to have all three displays.

I have a Dell Latitude D630 + a dock, with WinXP, it can't do all three displays simultaneously.  At most, I can select any combination of two displays.

---

### Post by kylepike on 2008-03-27
Did you ever find a solution for this? Myself and everyone I work with have D630's, and they are use 2 monitors in vista or xp. 

I keep getting 

"• MetaMode 1 of Screen 0 has more than two active display devices." and I can't figure out what the hell to do.

but if anyones found a solution for this PLEASE let me know!!!

---

### Post by chewearn on 2008-03-27
No, like I said previously, I don't think it's possible.  I'm pretty sure, because I run WinXP in the D630, and the latest dell-intel video driver configuration only support up to two simultaneous displays.  See screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64108&stc=1&d=1206670229[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=64109&stc=1&d=1206670459[/IMG]

You can see, while three displays are detected, it only allow you to choose any two at one time.

---

