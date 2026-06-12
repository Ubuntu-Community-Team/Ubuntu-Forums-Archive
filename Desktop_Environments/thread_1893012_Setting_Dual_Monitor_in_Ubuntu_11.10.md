---
title: "Setting Dual Monitor in Ubuntu 11.10"
date: 2011-12-09
forum: Desktop Environments
---

### Post by silentray on 2011-12-09
I have difficulty in setting dual monitor on Ubuntu 11.10.

I have successfully setup both monitors but there are one remaining problems:

One of my monitor's resolution is 1280x1024, however, it can only work under 1024 x 768. How can I force the resolution?

Here is my xorg.conf:

    Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" LeftOf "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
        Option         "Xinerama" "1"
    EndSection
    
    Section "Files"
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
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 60.0
        Option         "DPMS"
    EndSection
    
    Section "Monitor"
        Identifier     "Monitor1"
        VendorName     "Unknown"
        ModelName      "CRT-1"
        HorizSync       28.0 - 55.0
        VertRefresh     43.0 - 72.0
    EndSection
    
    Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GTS 240"
        BusID          "PCI:1:0:0"
        Screen          0
    EndSection
    
    Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GTS 240"
        Option         "rotate" "left"
        BusID          "PCI:1:0:0"
        Screen          1
    EndSection
    
    Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "DFP: 1920x1080 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "CRT: nvidia-auto-select @1280x1024 +0+0"
        SubSection     "Display"
            Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
        EndSubSection
    EndSection
    
    Section "Extensions"
        Option         "Composite" "Disable"
    EndSection

---

### Post by BC59 on 2011-12-09
To show what resolutions are currently supported for your display run this on a terminal:

```
xrandr
```

To change resolution follow the instructions here:

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

---

