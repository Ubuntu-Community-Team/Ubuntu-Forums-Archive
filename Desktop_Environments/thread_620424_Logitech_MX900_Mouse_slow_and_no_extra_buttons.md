---
title: "Logitech MX900 Mouse slow and no extra buttons"
date: 2007-11-22
forum: Desktop Environments
---

### Post by stony on 2007-11-22
Hello Ubuntu and Community,
so, i finally made it. got my system running a dual boot with WinXp and Gutsy Gibbon and thus i found my first problems i couldn't figure out myself.

ok, now to the problems:
I have a Logitech Cordless Elite (bluetooth) keyboard and a MX900 (bluetooth) Mouse with that.

I couldn't use them to install Ubuntu so i just connected another usb-mouse and a simple ps/2 keyboard for the installation untill i had everthing up and running.

Connecting the bluetooth keyboard and mouse (and headset) was a breeze following another thread i found yesterday. They even  survive reboots. no problem at all.
I did already install lirc as i want my PackardBell remote working under linux just as i can under winXP (switching tv channels, volume up and down, controlling dvd, amarok,.... quite a setup i managed with girder ;) )

Problem 1: The MX900 is like very slow. Put the sensitivity all the way up.
tried setting the resolution to 800dpi with logitech-applet to no avail.
tried setting the resolution to 800dpi with lomoco to no avail.
This is kind of annoying running a dual screen (2x 19") twinview setup.
I suspect there is something wrong with my /proc/bus/input/devices as there are way to many devices showing up judging by all the other tutorials out there. How can this be fixed?

Problem 2:
I got so used to using the extra buttons on my mouse (running windows) that i just need them back. Because i'm a Webdeveloper i got one set to back and the other one to refresh. How can i set this up in Ubuntu?

optional Problem 3:
While we're at it, how i can i set my extra buttons on the keyboard to controll amarok and maybe launch some other Application (to be honest, i didn't look into that one yet (blush) ) Volume and Mute buttons are already working thou.
Any pointers appreciated.

```
lomoco -s
002.001: 0000:0000 Not a Logitech device
001.013: 046d:c707 Unsupported Logitech device: Unknown
001.011: 0451:2036 Not a Logitech device
001.012: 046d:c703 Unsupported Logitech device: Unknown
001.008: 04b4:fd11 Not a Logitech device
001.010: 10ab:10c5 Not a Logitech device
001.009: 05fe:0011 Not a Logitech device
001.001: 0000:0000 Not a Logitech device

```

```
cat /proc/bus/input/devices 
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05fe Product=0011 Version=0110
N: Name="Cypress Semi. Cypress Ultra Mouse"
P: Phys=usb-0000:00:02.0-5/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-9.1/input0
S: Sysfs=/class/input/input6
U: Uniq=0D816D
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-9.1/input1
S: Sysfs=/class/input/input7
U: Uniq=0D816D
H: Handlers=kbd mouse2 event4 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 f80 8837c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input9
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input10
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0005 Vendor=046d Product=b001 Version=2200
N: Name="Logitech MX900 Mouse"
P: Phys=00:07:61:0D:81:6D
S: Sysfs=/class/input/input11
U: Uniq=00:07:61:0A:62:77
H: Handlers=mouse3 event8 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b301 Version=2303
N: Name="Logitech Elite Keyboard"
P: Phys=00:07:61:0D:81:6D
S: Sysfs=/class/input/input12
U: Uniq=00:07:61:08:15:01
H: Handlers=kbd mouse4 event9 
B: EV=12000f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 10f80 8837c007 ffe67bfa d941dfff febeffdf ffefffff ffffffff fffffffe
B: REL=143
B: ABS=301 0
B: LED=1f

```

```
cat /etc/X11/xorg.conf (well, the important stuff atleast
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX900 Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Logitech MX900 Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "false"
EndSection

```

xorg.conf is modified manually because i tried to solve it on my own, but i'm not really that experienced with linux yet.

If you need more information i reply as soon as possible. Hope someone can help me out here;)

Thanks
stony

---

### Post by zebrankyza on 2007-11-25
Hey stony,

Can't answer all your questions (pretty new to Ubuntu myself), but I did manage to get some degree of happiness out of [this link]("http://ubuntuforums.org/showthread.php?p=2727025").  This will probably only help with your mouse itself (for the keyboard shortcuts etc. Your "Problem 2" :))  I have the MX Revolution, and the solution in the link worked pretty okay, although I was having intermittent problems that I have not looked into yet.

Cheers
Brian

---

### Post by stony on 2007-11-27
found this:
[http://ubuntuforums.org/archive/index.php/t-59729.html]("http://ubuntuforums.org/archive/index.php/t-59729.html")

seamed pretty useful (at first).

unfortunately after i adjust my xorg.conf my x-server didn't like it at all. always tries to load default configurations ](*,)

another thing i notices, my mouse just keeps changing names. The linked thread mentions i should use the name from "cat /proc/bus/input/devices" in my xorg.conf under the section "inputDevice" like
Option "Dev Name" "Logitech Bluetooth Mouse"

sometimes the name in /proc/bus/input/devices is "Logitech Bluetooth Mouse", sometimes it's referred to as "Logitech MX900 Mouse" and some other combinations as well.

would be glad if some experienced user could check my xorg.conf


[CODE cat /etc/X11/xorg.con 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
    Load           "i2c"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
        Identifier     "Mouse0"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "evdev"
        Option "Buttons" "10"
        Option "ZAxisMapping" "9 10"
        Option "Dev Name" "Logitech Bluetooth Mouse"
        Option "Dev Phys" "00:07:61:0A:62:77"
        Option "Resolution" "800"
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
    ModelName      "BenQ FP93GX"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024_75 +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/CODE]

> cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05fe Product=0011 Version=0110
N: Name="Cypress Semi. Cypress Ultra Mouse"
P: Phys=usb-0000:00:02.0-5/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-9.1/input0
S: Sysfs=/class/input/input3
U: Uniq=0D816D
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-9.1/input1
S: Sysfs=/class/input/input4
U: Uniq=0D816D
H: Handlers=kbd mouse2 event4 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 f80 8837c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0005 Vendor=046d Product=b001 Version=2200
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:0D:81:6D
S: Sysfs=/class/input/input8
U: Uniq=00:07:61:0A:62:77
H: Handlers=mouse3 event8 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b301 Version=2303
N: Name="Logitech Bluetooth Keyboard"
P: Phys=00:07:61:0D:81:6D
S: Sysfs=/class/input/input9
U: Uniq=00:07:61:08:15:01
H: Handlers=kbd mouse4 event9 
B: EV=12000f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 10f80 8837c007 ffe67bfa d941dfff febeffdf ffefffff ffffffff fffffffe
B: REL=143
B: ABS=301 0
B: LED=1f


---

