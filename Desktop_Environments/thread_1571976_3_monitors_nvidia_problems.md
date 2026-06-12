---
title: "3 monitors nvidia problems"
date: 2010-09-10
forum: Desktop Environments
---

### Post by ctrt on 2010-09-10
Hi, I've recently got a new TV so wanted to use it as another monitor on top of two monitors setup in twinview. I'm using two nvidia 8800gt, one connected to the 2 monitors and the other to the TV.
 I've started by trying to create separate x on each screen but one screen always hangs on the pink login screen whilst the other two seem to work fine. 
I've tried swaping the cards around and moving the monitors around with respect to each other (ie. screen1 right of screen0; screen2 below screen0). I've tried using different drivers from the hardware drivers program, the nvidia recommended and then I've used the nvidia 173 driver but installed by using 'sudo apt-get install nvidia-glx-173'. Both have exactly the same problems. Weirdly the hardware driver program says nvidia_173 and nvidia_current are both activated but not in use??

Heres the my xorg setup-




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" Below "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
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
    ModelName      "HP2159"
    HorizSync       24.0 - 94.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP2159"
    HorizSync       24.0 - 94.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       26.0 - 81.0
    VertRefresh     24.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"


    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"


    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"


    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Does anybody have a clue how to resolve this? I'm thinking its a driver problem? 

I'm using 10.04 btw.

Many thanks

---

### Post by ctrt on 2010-09-10
Forgot to add wasn't using twinview because it would maximize windows across both screens. Thats kind of been solved through following this - 
[http://superuser.com/questions/65989/ubuntu-9-10-3-monitors-setup](http://superuser.com/questions/65989/ubuntu-9-10-3-monitors-setup)

Still have the problem of the 3rd screen hanging on login screen. Used glxinfo to try and find out the driver I'm actually using.

One of the things it outputted was


OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GT/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler

Does this mean I'm actually using driver 195?

In the hardware drivers program tried to disable nvidia-current and left nvidia-173 activated (although it still says activated but not used) but it then threw an error 'no proprietary driver in use' and crashed..

Anyone have any ideas, experienced this before? I'm kinda a linux novice so any help would be appreciated..

---

