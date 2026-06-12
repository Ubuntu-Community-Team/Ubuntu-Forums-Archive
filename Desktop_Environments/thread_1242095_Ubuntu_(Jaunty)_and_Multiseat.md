---
title: "Ubuntu (Jaunty) and Multiseat"
date: 2009-08-16
forum: Desktop Environments
---

### Post by knight187 on 2009-08-16
Ubuntu (Jaunty) and Multiseat

Let me start with saying that I know their are some really good articles and posts out there about  how to setup multiseat. I am writing this because I couldn't find one that was a complete setup that included compiz desktop effects, sound and bug fixes for each terminal. It has taken me days to workout all the bugs and get a proper working desktop for 2 users off 1 PC, this includes sound for each users and desktop effects.

My config uses Jaunty (32bit), 2 x Nvidia GPU's, 2 sound cards, Intel E8500 CPU (3.16GHz), 4GiB RAM.

Most of my information I used to get my multiseat setup running was from this page ([https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)) but this config did not allow for either of the desktops to have Compiz desktop effects because it sets up a X session across both the GPU's and then sets up 2 nested X sessions inside that "dummy" X session. I have no idea why the author of this page has decided to do this, but I'm no expert so maybe there's a reason that I haven't found yet or maybe its how older versions of X needed to be setup for multiseat. Anyway to get compiz running on multiseat you just need to take out the dummy X session and just setup 2 independient X sessions each with its own keyboard and mouse. This is my xorg.conf


```
Section "ServerLayout"
        Identifier      "Seat.0"
        Screen          "Screen.0.0"
        InputDevice     "Keyboard.0" "CoreKeyboard"
        InputDevice     "Mouse.0" "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Seat.1"
        Screen          "Screen.1.0"
        InputDevice     "Keyboard.1" "CoreKeyboard"
        InputDevice     "Mouse.1" "CorePointer"
EndSection

Section "Extensions"
    Option         "RENDER"       "True"
    Option         "DAMAGE"       "True"
    Option         "Composite"    "True"
EndSection

Section "Module"
    Load           "dbe"
    Load           "glx"
    SubSection     "extmod"
        Option     "omit xfree86-dga"
    EndSubSection
EndSection

Section "ServerFlags"
    Option         "RandR"        "True"
    Option         "AllowDeactivateGrabs" "true"
    Option         "DontZap" "True"
    Option         "DefaultServerLayout" "seat0"
    Option         "AllowMouseOpenFail"  "true"
    Option         "AutoAddDevices"      "false"
    Option         "AutoEnableDevices"   "false"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "void"
EndSection

Section "InputDevice"
    Identifier    "Generic Mouse"
    Driver        "void"
EndSection

Section "InputDevice"
        Identifier      "Keyboard.0"
        Driver          "evdev"
    Option          "Name"         "Microsft Microsoft Wireless Desktop Receiver 3.1A"
        Option          "Device"        "/dev/input/by-id/usb-Microsft_Microsoft_Wireless_Desktop_Receiver_3.1A-event-kbd"
EndSection

Section "InputDevice"
        Identifier      "Mouse.0"
        Driver          "evdev"
    Option          "Name"         "Microsft Microsoft Wireless Desktop Receiver 3.1A"
        Option          "Device"        "/dev/input/by-id/usb-Microsft_Microsoft_Wireless_Desktop_Receiver_3.1A-event-joystick"
EndSection

Section "InputDevice"
        Identifier      "Keyboard.1"
        Driver          "evdev"
        Option          "Name"          "Microsoft Natural&#65533; Ergonomic Keyboard 4000"
        Option          "Device"        "/dev/input/by-id/usb-Microsoft_Natural__Ergonomic_Keyboard_4000-event-kbd"
EndSection

Section "InputDevice"
        Identifier      "Mouse.1"
        Driver          "evdev"
        Option          "Name"          "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
        Option          "Device"        "/dev/input/by-id/usb-Microsoft_Microsoft_5-Button_Mouse_with_IntelliEye_TM_-event-mouse"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips 190SW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "GeForce 8800 Ultra"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 Ultra"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "GeForce 9400 GT"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen.0.0"
    Device         "GeForce 8800 Ultra"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Coolbits"                 "1"
    Option         "NoLogo"                   "True"
    Option         "CursorShadow"             "True"
    Option         "RenderAccel"              "True"
    Option         "AddARGBGLXVisuals"        "True"
    Option         "ConnectToAcpid"           "False"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen.1.0"
    Device         "GeForce 9400 GT"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Coolbits"                 "1"
    Option         "NoLogo"                   "True"
    Option         "CursorShadow"             "True"
    Option         "RenderAccel"              "True"
    Option         "AddARGBGLXVisuals"        "True"
    Option         "ConnectToAcpid"           "False"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

As you can see from the xorg.conf I have 2 server layouts each with a GPU, monitor, keyboard and mouse. It really is that easy.....  The final thing you have to do to get your base multiseat setup working is modify your /etc/gdm/gdm.conf-custom. This is mine

```
[daemon]
VTAllocation=false

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Seat0
1=Seat1

[server-Seat0]
name=Seat 0 server
command=/usr/bin/X -br -audit 0 -layout Seat.0 -sharevts -novtswitch vt09
flexible=false

[server-Seat1]
name=Seat 1 server
command=/usr/bin/X -br -audit 0 -layout Seat.1 -sharevts -novtswitch vt09
flexible=false
```

Once you have done this you can reboot and you should have a working multiseat setup with compiz desktop effects. So now moving onto sound. To get the sound to work for each workstation I installed a second sound card and speakers and to control where the sound would play for each desktop I installed "padevchooser" (Pulse Audio Device Chooser) once this package is installed and running goto the Preferences and choose start application at login. Then goto Volume control, output devices, right click on the device you want from this terminal and select default. Do the same for the second terminal, logout and back in and you should have your own sound playing from your own speakers on your seat of the multiseat computer.

Now you sould have a working multiseat setup with Compiz and Sound on each Seat.

After setting up multiseat I had some keyboard problems on both seats eg. extra buttons on the top of the keyboards were now not working and the Left and Down arrow had lost there repeat function to fix the repeat problem I had to run this command from the terminal

xset r 113; xset r 116

I just put this in a file called keyboard-fix.sh and added it to my start up applications so it would run at login. don't forget to chmod +x it so it can execute. To fix the extra keyboard buttons I had to select my keyboard model from the Layout Tab of the system -> Preferences -> keyboard application. Now my keyboard works perfectly but unfortunately the keyboard on the other seat on my multiseat system is a "Microsoft Natural Ergonomic Keyboard 4000" and there is no selection for this keyboard on the keyboard application so I still cant get the extra buttons working on this keyboard but there must be a way because when I use this keyboard on a standard install of Jaunty all the functions on the keyboard seem to work fine. If anyone out there has a solution for this keyboard I would be keen to here it.

Anyway, Cheers all and good luck, feel free to contact me if you have any issues setting any of this up I am happy to help.

Note: you can even run network games on each seat against each other.  Now that's cool....

EDIT: I found a solution to my Microsoft 4000 Keyboard, apparently this keyboard is 2 devices in one, 1 device is the normal keys and the second device is the extra keys ([http://www.gentoo-wiki.info/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000](http://www.gentoo-wiki.info/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000))

---

### Post by MattiJ on 2009-08-28
Thanks very helpful!

---

### Post by infallible on 2009-09-16
I have two monitors: one w/ 1080p max resolution, and one with a standard aspect ratio. How should I configure my display / virtual display resolution?

---

### Post by knight187 on 2009-09-16
> **infallible said:**
> I have two monitors: one w/ 1080p max resolution, and one with a standard aspect ratio. How should I configure my display / virtual display resolution?

Jaunty is really good at auto detecting the screen resolution for you, I haven't had to set any resolutions for my setup.  I have 1 screen displaying 1920x1200 and the second seat is 1440x900. 

In my experience xorg had just detected the resolution for any display device I have ever tried.

Please let us know if you need more help then this, and if you do, please provide hardware details and errors from logs so we can pass on the correct information.

Cheers Mate and good luck, let us know if you get it working.

---

### Post by dampierre on 2009-09-25
Does it work with one card and two monitors?
I have an Acer LCD and a Philips TV on an ATI HD4850.
I cannot separate the two desktops. I think X draws the desktops over each other, but both outputs show almost the same picture.

These are the pertinenet lines from my xorg.conf :

```
[SIZE=1]Section "Device"
    Identifier  "Card0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "Acer"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "fglrx"
    Option        "Monitor-DFP_EXTTMDS" "Philips"
    BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier   "Acer"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "Philips"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x720"
    Option        "TargetRefresh" "50"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Acer"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Philips"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "ServerFlags"
    Option       "DontVTSwitch" "yes"
    Option         "RandR"        "True"
    Option         "AllowDeactivateGrabs" "true"
    Option         "DontZap" "false"
    Option         "DefaultServerLayout" "Seat0"
    Option         "AllowMouseOpenFail"  "true"
    Option         "AutoAddDevices"      "false"
    Option         "AutoEnableDevices"   "false"
EndSection

Section "ServerLayout"
    Identifier     "Seat0"
    Screen         "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "Seat1"
    Screen         "Screen1" 0 0
        InputDevice    "Mouse1" "CorePointer"
        InputDevice    "Keyboard1" "CoreKeyboard"
EndSection[/SIZE]
```

---

### Post by snakekontrol on 2009-10-13
Hi, i have an Ubuntu 9.04 workstation, with two ati video cards connected through pci-express, i have 4 displays connected to the two cards (2xVGA 2xDVI) i have mannaged to get a multiseat with 2 heads, but i can't ake it work for 4 heads, i hope you can help me, here are my xorg.conf and gdm.conf configurations, thanks!!!

XORG.CONF
> Section "ServerLayout"
    Identifier     "Layout1"
    Screen      0   "Screen1" 0 0
    InputDevice    "Mouse1" "CorePointer"
    InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "Layout2"
    Screen         "Screen2" 
    InputDevice    "Mouse2" "CorePointer"
    InputDevice    "Keyboard2" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "Layout3"
    Screen         "Screen3" 0 0
    InputDevice    "Mouse3" "CorePointer"
    InputDevice    "Keyboard3" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "Layout4"
    Screen         "Screen4" RightOf "Screen3"
    InputDevice    "Mouse4" "CorePointer"
    InputDevice    "Keyboard4" "CoreKeyboard"
EndSection



Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
    Option        "DefaultServerLayout" "Layout1"
    Option        "AllowMouseOpenFail" "true"
    Option        "AutoAddDevices" "false"
    Option        "AutoEnableDevices" "false"
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    Driver      "evdev"
    Option        "Device" "/dev/input/event3"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier  "Keyboard2"
    Driver      "evdev"
    Option        "Device" "/dev/input/event7"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier  "Keyboard3"
    Driver      "evdev"
    Option        "Device" "/dev/input/event10"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier  "Keyboard4"
    Driver      "evdev"
    Option        "Device" "/dev/input/event11"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "es"
EndSection





Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "mouse"
    Option        "Protocol" "ExplorerPS/2"
    Option        "Device" "/dev/input/mouse1"
    Option        "ZAxisMapping" "6 7"
EndSection

Section "InputDevice"
    Identifier  "Mouse2"
    Driver      "mouse"
    Option        "Protocol" "ExplorerPS/2"
    Option        "Device" "/dev/input/mouse2"
    Option        "ZAxisMapping" "6 7"
EndSection

Section "InputDevice"
    Identifier  "Mouse3"
    Driver      "mouse"
    Option        "Protocol" "ExplorerPS/2"
    Option        "Device" "/dev/input/mouse3"
    Option        "ZAxisMapping" "6 7"
EndSection

Section "InputDevice"
    Identifier  "Mouse4"
    Driver      "mouse"
    Option        "Protocol" "ExplorerPS/2"
    Option        "Device" "/dev/input/mouse4"
    Option        "ZAxisMapping" "6 7"
EndSection


Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[2]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "Monitor4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "Device2"
    Driver      "fglrx"
#·    Option        "Monitor-CRT2" "Monitor2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Device3"
    Driver      "fglrx"
#    Option        "Monitor-CRT1" "Monitor3"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "fglrx"
#    Option        "Monitor-CRT1" "Monitor1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Device4"
    Driver      "fglrx"
#    Option        "Monitor-CRT2" "Monitor4"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    Monitor    "Monitor1"
    DefaultDepth     24
    SubSection "Display"
        Virtual  5120 1024
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Device2"
    Monitor    "Monitor2"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Device3"
    Monitor    "Monitor3"
    DefaultDepth     24
    SubSection "Display"
        Virtual  2560 1024
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen4"
    Device     "Device4"
    Monitor    "Monitor4"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection


GDM.CONF

> 0=Standard0
1=Standard1
2=Standard2
3=Standard3

[server-Standard0]
name=Standard server
command=/usr/X11R6/bin/X -nolisten tcp -novtswitch -sharevts -layout Layout1
flexible=false

[server-Standard1]
name=Standard server
command=/usr/X11R6/bin/X -nolisten tcp -novtswitch -sharevts -layout Layout2
flexible=false

[server-Standard2]
name=Standard server
command=/usr/X11R6/bin/X -nolisten tcp -novtswitch -sharevts -layout Layout3
flexible=false

[server-Standard3]
name=Standard server
command=/usr/X11R6/bin/X -nolisten tcp -novtswitch -sharevts -layout Layout4
flexible=false



I really hope you can help me, the 2 heads shows one on each card, and the other 2 displays just run on mirror mode, any thoughts?

---

### Post by knight187 on 2009-10-13
Hi dampierre,

This is the link I tried to follow to get Multiseat working from 1 card

[http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html](http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html)

But I failed....

good luck,

Cheers, Bruce

---

### Post by knight187 on 2009-10-13
Hi snakekontrol, I have never been able to get 2 seats working from 1 dual head card, I tried for days before giving up and buying a second vid card for the second seat.

This is the link I tried to follow to get Multiseat working from 1 card

[http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html](http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html)

If you succeed in getting 2 seats from 1 card maybe you can expand that to 4 seats on 2 cards.

good luck, let me know if you get it all to work.

Cheers, Bruce

---

### Post by snakekontrol on 2009-10-14
Hi knight187 i have followed the tutorial you posted before, i made it work with 1 card and two displays, but i can't make it work for the second card and the other 2 displays, my thoughts are that the Xephyr-login.sh script has to be reconfigured in order to make the 4 displays work, but i don't have the knowledge to modify it, any other thoughts? thanks!!!!

---

