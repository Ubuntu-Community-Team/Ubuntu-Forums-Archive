---
title: "Triple Monitor setup.. Need Help With Drivers and Card"
date: 2009-12-20
forum: Desktop Environments
---

### Post by Neogenics on 2009-12-20
Hi All,

Ok this is going to be a little wordy of an explanation but, I am trying to include all of the information i have. I am trying to use Three monitors with my desktop ubuntu right now. I have two different cards that i have tried using (both support two monitors and i have tried using them SEPERATELY). One is an ATI Radeon X13 and the other is an nVidia Geforce 9600. Those being seperate brands is the reason i have been trying them seperately and not together. Now either one  of those cards works fine and that sets me with two monitors. Both of them i can get the drivers working fine. The third monitor i am trying to use with the on board video support (now let me explain before you say it cant be done). The onboard chipset (according to lspci -nn | grep VGA, copy and pasted) is  nVidia Corporation GeForce 6150SE nForce 430. Now i have previously used the ATI with this onboard video to have three working monitors in Windows (I know horrors) so I know that it can be done. I would prefer to use the geforce card because it's a much nicer and newer card but i can settle if I can just get the three monitors to work. My motherboard is a Gigabyte GA-M61P-S3 AM2. Can anybody please help me with this problem? i have been trying literally for months to get this working and i am at my wits end on how to do this. Please don''t tell me i found a way to do this in windows and i have found a reason to like windows better than linux... Help somebody?

Thank you in advance,
Neo

---

### Post by Neogenics on 2009-12-20
I don't like to do this much.. but the thread had dropped a few pages and it's been almost a day. Hopeful I can get an answer

*bump*

---

### Post by Neogenics on 2009-12-21
another 24hrs.. another bump

---

### Post by schmolch on 2009-12-22
It can be easily done.
I use a triple-monitor setup myself with a onboard-nvidia and a dualhead pci-e nvidia.
What brand your cards are does not matter as long as they work individually. 
You have to do your xorg.conf yourself though because no gui-tool is able to do that yet.
You will also not be able to use compiz and might experience a slowdown of your Desktop.
Here is my xorg.conf:
```



Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen 	2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    ModelName      "NEC LCD2070NX"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "NEC LCD2070NX"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / nForce 630a"
    BusID          "PCI:0:18:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
    Screen 0  # <- i need this because its a dualhead-card
EndSection


Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
    Screen 1  # <- i need this because its a dualhead-card
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"  
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-2: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
I see that i have some mistakes in it with only 2 monitors declared and monitor2 not even existing. Interesting that it still works.


Feel free to ask if you have any further questions.

---

