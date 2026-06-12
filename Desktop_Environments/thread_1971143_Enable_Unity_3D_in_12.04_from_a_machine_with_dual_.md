---
title: "Enable Unity 3D in 12.04 from a machine with dual screens run by two nvidia cards"
date: 2012-05-02
forum: Desktop Environments
---

### Post by diablo465 on 2012-05-02
Hi folks: 
   My goal is to enable Unity 3D in 12.04 from a machine having two monitors respectively connected to two nvidia Video cards, and one of the monitors rotate clock wisely . However, I found it is really hard. so far what I can achieve is to have dual screen in Unity 2D with one rotated monitor by using the following script:

$ sudo gedit /etc/X11/xorg.conf 
[COLOR="Red"]
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "ServerFlags"
    # Not working with Xinerama anyways.
    Option    "RandR" "on"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2208WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2209WA"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 580"
    BusID          "PCI:3:0:0"
    Option	"NoLogo"	"True"
    Option          "Rotate" "left"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 580"
    BusID          "PCI:4:0:0"
    Option	"NoLogo"	"True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection[/COLOR]

the problem of this setting is:
1. only working in Unity 2D
$ echo $DESKTOP_SESSION
ubuntu-2d
2. nothing comes up when execute 
   $  /usr/lib/nux/unity_support_test -p
Error: no composite extension
3. $ ps -ef | grep compiz | grep $USER
chenming  2547  2380  0 20:15 pts/1    00:00:00 grep --color=auto compiz
3. compiz does not work, either.

I also saw my colleague using the following script to enable unity 3D in 12.04 from a machine with dual screen without rotating

[COLOR="Red"]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U2312HM"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro 4000"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/COLOR]

but clearly the difference between his machine and mine is that he has got one video card with two sockets, therefore only one device is defined, and dual screen can be achieved by TwinView rather than Xinerama. But in my case all of the devices, monitors has to define twice. and so far as I know it might not working by using TwinView. Also I didn't know whether TwinView can rotate screen. Is there any way i can do to enable unity 3d in my machine with two video cards and screens? thanks a lot!

---

### Post by diablo465 on 2012-05-07
After some time digging about this problem, I think this is currently not solvable. Unity 3D is supported by Composite, while Xinerama is not compatible with Composite. While the only way to use dual screens that respectively connected to two video cards is Xinerama, therefore unity 3D can not work. 

my colleague can use dual screen with unity 3d is because his screens are all connected to one video card. in that case Twinview, rather than Xinerama can be applied. The former one seems to be a trend. 

After using Ubuntu for 2 month, I realized that one should be aware of hardware driver problems which is taken for granted in windows. Double check the compatibility of the hardware to ubuntu before making a purchase decision!

hope to get some more opinions!

---

### Post by xirrin on 2012-05-16
ethan@RODGERS:~$ echo $DESKTOP_SESSION
ubuntu-2d
ethan@RODGERS:~$ /usr/lib/nux/unity_support_test -p
Error: no composite extension
ethan@RODGERS:~$ ps -ef | grep compiz | grep $USER
ethan     4102  4034  0 21:50 pts/0    00:00:00 grep --color=auto compiz
ethan@RODGERS:~$ 

I am having the exact same issues that you are. I am running 3 monitors all in normal landscape mode with none rotated. I'm hoping someone may have an answer for this?

---

