---
title: "gdm login dialog not on the 'primary display'"
date: 2012-06-17
forum: Desktop Environments
---

### Post by petru.marginean on 2012-06-17
Hi,

I just switched to using dual monitor setup. Everything works fine, but the gdm login dialog doesn't appear on the 'primary display'.

This is an inconvenience to me, since I would like to keep the second monitor turned off (to save energy), and only turn it on when I really need it. 

 My 'primary display for X screen' is 'Acer G23H' (1920x1080, using DVI output), the second monitor is 'Dell E228WFP' (1680x1050, using VGA output).

The graphic card is  "GeForce 8400 GS".
(JATON Video-PX8400GS_LX GeForce 8400 GS 256MB 64-bit GDDR2 PCI Express x16 Low Profile Video Card)

I've tried multiple display managers (kdm, slim, xdm, wdm, ldm) but I still like gdm best. (Note all the other display managers put the login dialog on the 'primary display')

I use ubuntu 12.04, gnome 3.2.1:

```

$> gnome-session --version
gnome-session 3.2.1

$> uname -a
Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux

```I have no errors in the log file:

```
$> grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 47340.434] (II) Loading extension MIT-SCREEN-SAVER

```Here is my xorg.conf file:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection
Section "Files"
EndSection
Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer G235H"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E228WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1920+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection
Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection
Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```Please help,
PM

---

### Post by petru.marginean on 2012-06-20
Hi,
I currently have version 3.0.4 of gdm:
```
$> /usr/sbin/gdm --version
GDM 3.0.4
```I've tried to install a newer version of gdm, but I got this error:

```
$> cd gdm-3.4.0
$> ./configure
//...
checking for COMMON... yes
checking for DAEMON... no
configure: error: Package requirements (dbus-glib-1 >= 0.74
        gobject-2.0 >= 2.29.3
        gio-2.0 >= 2.29.3
        accountsservice >= 0.6.12
) were not met:

No package 'accountsservice' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DAEMON_CFLAGS
and DAEMON_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```How can I resolve this error?
It looks like the accountsservice is installed in /usr/lib:

```
$> locate accountsservice
/usr/lib/accountsservice
/usr/lib/libaccountsservice.so.0
//...

```but the *.pc file is missing.

Regards,
PM

---

### Post by petru.marginean on 2012-07-17
I 'solved' this by switching to lightdm.

---

