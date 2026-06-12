---
title: "Unable to move windows and terminal appears as white box without text"
date: 2008-12-02
forum: Desktop Environments
---

### Post by D!mSome on 2008-12-02
Greetings,

I recently installed ubuntu 8.10.  After installing ubuntu I installed restricted driver support for a Nvidia 420 graphics card.  After using the Nvidia application to adjust resolution I can't move or resize open windows.  Also, when I launch terminal it only appears as a white box with no text.  I'm wondering if i'm missing a setting in xorg.conf

This was my Xorg config before adjusting resolution.  The resolution was at an unbearable 640x480

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

And here is my current xorg.conf

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL D1025HT"
    HorizSync       30.0 - 85.0
    VertRefresh     48.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 420"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Am I missing something?

---

### Post by Zorael on 2008-12-03
Hum, that xorg.conf is a mess. Have you tried regenerating a fresh one?

```
$ cd /etc/X11
$ sudo mv xorg.conf xorg.backup0812
$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo nvidia-xconfig -d 24 --add-argb-glx-visuals --randr-rotation
```

With TwinView, I don't think you need more than that? Anyway, backup first.

---

### Post by D!mSome on 2008-12-04
Thanks for the reply.  It seems I am missing a component of xserver-xorg

Heres what happens when I type:
sudo dpkg-reconfigure -phigh xserver-xorg

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

So I try to install xserver-org with APT:

sudo apt-get install xserver-xorg

Reading package lists...
Building dependency tree...
Reading state information...
xserver-xorg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is there something else I need to install?

---

