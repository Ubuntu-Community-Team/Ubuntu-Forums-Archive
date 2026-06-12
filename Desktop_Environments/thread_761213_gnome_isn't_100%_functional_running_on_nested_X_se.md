---
title: "gnome isn't 100% functional running on nested X server (Xgl or Xephyr)"
date: 2008-04-21
forum: Desktop Environments
---

### Post by mktmccoy on 2008-04-21
I'm running 64bit Hardy Heron with all updates with a Nvidia 8600GT dual-head card.  Everything works fine when my X server is in a dual monitor single seat configuration.  Most things work in multiseat/multi-terminal,  but there are some annoying glitches in this configuration.  

Some of the gitches are 
1) gdmgreeter crashes at startup, so gdm falls back to gdmlogin, which works fine.
2) gnome administration apps like users-admin (Users and Groups), network-admin (Network) become un-usable because the Unlock button is grayed out.

[INDENT]If I try to run it from the command line, I get the following error
> sudo users-admin

** (users-admin:13807): CRITICAL **: Unable to lookup session information for process '13807'
[/INDENT]

3) Can't suspend the system (Suspend to RAM).  My screen saver kicks in asking for my password, so I type it in and it returns to my desktop.  I can suspend the system in single seat mode.

Does anybody know what is wrong?  I'm wondering if these gnome admin apps assume they are running on the Xorg server and get confused when running Xgl or Xephyr.

Here are some details about multi-seat setup

[FONT="Courier New"][SIZE="2"]xorg.conf

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1280 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/null"
#    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option          "XkbRules"      "xorg"
    Option          "XkbModel"      "evdev"
    Option          "XkbLayout"     "us"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 160.0
    Option         "DPMS"
EndSection
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "RenderAccel" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "RenderAccel" "true"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


gdm.conf
# everything else is default except this part.
[servers]
0=MainServerXephyr
1=Xephyr1
2=Xephyr2

[server-MainServerXephyr]
name=MainServerXephyr
command=/usr/bin/X -br -audit 0 -dpms -s 0
handled=false
flexible=false

[server-Xephyr1]
name=Xephyr1
command=/usr/sbin/Xephyr-path.sh -display :0.0 -br -xauthority /var/lib/gdm/:0.Xauth -kbdpath /dev/input/by-id/usb-Logitech_USB_Receiver-event-kbd -mousepath /dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse -softCursor -fullscreen -ac
handled=true
flexible=false

[server-Xephyr2]
name=Xephyr2
command=/usr/sbin/Xephyr-path.sh -display :0.1 -br -xauthority /var/lib/gdm/:0.Xauth -kbdpath /dev/input/event1 -mousepath /dev/input/by-id/usb-Microsoft_Microsoft_Wheel_Mouse_Optical-event-mouse -fullscreen -ac
handled=true
flexible=false

[/SIZE][/FONT]

/usr/sbin/Xephyr-path.sh is a simple wrapper that 

     export XAUTHORITY="$1"
     export DISPLAY="$1"

and executes the following command.

[INDENT]/usr/bin/Xephyr :2 -br -keybd evdev,,device=/dev/input/event1,xkbrules=xorg,xkbmodel=evdev,xkblayout=us -mouse evdev,,device=/dev/input/by-id/usb-Microsoft_Microsoft_Wheel_Mouse_Optical-event-mouse,WHEELRelativeAxisButtons 4 5 -fullscreen -ac -auth /var/lib/gdm/:2.Xauth -nolisten tcp vt9
[/INDENT]

---

