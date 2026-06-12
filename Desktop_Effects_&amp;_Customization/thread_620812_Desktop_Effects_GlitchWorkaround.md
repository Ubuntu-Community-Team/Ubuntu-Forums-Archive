---
title: "Desktop Effects Glitch/Workaround"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by francofran18 on 2007-11-23
Hey, this is annoying me heaps,

I have an Intel Chipset family 9*5 (sorry i can't remember the middle number):guitar:, and desktop effects won't work, 

now... desktop effects are the only reason i "upgraded" to Ubuntu 7.10 today, so my mates would all go "WOW", but there is no "WOW" in "desktop effects could not be enabled"

PLEASE help ASAP, my e-mail is [email]jayjay2601@hotmail.com[/email] or just post here,

greatly appricated, I'll give as much info as you want

---

### Post by FuturePilot on 2007-11-23
Could you post the output of
```
compiz --replace
```
from a terminal? Usually it will show what might be going wrong.

---

### Post by OOzypal on 2007-11-23
I have the same problem and desktop effect could not be enabled. Here is my

compiz --replace

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

My xorg conf

Section "Device"
    Identifier     "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce2 Integrated (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce2 Integrated (generic)"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

---

### Post by redtag on 2007-11-23
I'm seeing this error:

compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by francofran18 on 2007-11-23
it said that XGL was not installed or sumthing

---

### Post by Officer Dibble on 2007-11-23
Can you buy an Nvidia graphics card? My old 6600GT loved desktop effects, so I can personally recommend that spec upwards. Ubuntu is worth it. :cool:

> **francofran18 said:**
> Hey, this is annoying me heaps,

I have an Intel Chipset family 9*5 (sorry i can't remember the middle number):guitar:, and desktop effects won't work, 

now... desktop effects are the only reason i "upgraded" to Ubuntu 7.10 today, so my mates would all go "WOW", but there is no "WOW" in "desktop effects could not be enabled"

PLEASE help ASAP, my e-mail is [email]jayjay2601@hotmail.com[/email] or just post here,

greatly appricated, I'll give as much info as you want

---

### Post by ubuntukerala1980 on 2007-11-23
sudo apt-get install xserver-xgl


Can you try this

---

### Post by Forlong on 2007-11-23
> **OOzypal said:**
> Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Your graphics card has too less memory to work well with Compiz.
You can run it like this:
```
SKIP_CHECKS=yes compiz
``` but you will get black windows when opening more than a few at a time.
> **redtag said:**
> /usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
What graphics card and what version of Ubuntu are you using?
> **francofran18 said:**
> it said that XGL was not installed or sumthing
Can you please post the whole output?

---

### Post by francofran18 on 2007-11-23
> **kiran.bhaskaran.nair said:**
> sudo apt-get install xserver-xgl


Can you try this

okay i tried it aand i think i installed somthing, here is the output if you need it



[sudo] password for jay:
Sorry, try again.
[sudo] password for jay:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1843kB of archives.
After unpacking 4854kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libglitz1 0.5.6-1 [76.6kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB]
Fetched 1843kB in 13s (140kB/s)                                                
Selecting previously deselected package libglitz1.
(Reading database ... 89400 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by francofran18 on 2007-11-23
> **Forlong said:**
> Your graphics card has too less memory to work well with Compiz.
You can run it like this:
```
SKIP_CHECKS=yes compiz
``` but you will get black windows when opening more than a few at a time.

What graphics card and what version of Ubuntu are you using?

Can you please post the whole output?

HEY! thaks you made it work! i just did the skip check thing and it works fine now, i ahve had no problems and I'm a massive mulit - tasker, thankyou greatly... just in time too!

---

### Post by Forlong on 2007-11-24
Great, now open this:
```
gedit ~/.config/compiz/compiz-manager
```
put the command in there:
```
SKIP_CHECKS=yes compiz
```
and save.

Now you can use *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* to enable/disable Compiz.

---

### Post by ethanhunt on 2007-11-26
> **Forlong said:**
> Your graphics card has too less memory to work well with Compiz.
You can run it like this:
```
SKIP_CHECKS=yes compiz
``` but you will get black windows when opening more than a few at a time.

What graphics card and what version of Ubuntu are you using?

Can you please post the whole output?

This does not work for me. Here is my config
Dell 610 / Intel 915Gm chipset
Two external monitors connected.
xrandr works perfectly on my Gutsy so i have dual display.

When I run compiz it fails

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (2048): Failed.
Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Forlong on 2007-11-26
> **ethanhunt said:**
> ```
Comparing resolution (3200x1200) to maximum 3D texture size (2048): Failed.
```
Your graphics chip can't handle Compiz with two monitors on such a high resolution.

You could use two monitors with 1024x768 each, for example.

---

### Post by buck65 on 2007-11-30
Please help i have intel 965 mobile chipset in a dell inspiron 1520 laptop 

have done all the above workarounds with no joy

here's my latest output

will@Open-IT-Laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
will@Open-IT-Laptop:~$ 
will@Open-IT-Laptop:~$ 


I am an IT consultant and i know windows inside out - but i cant stand microsoft, hence am using ubuntu - but know jack about linux please help!!

:)

---

### Post by Forlong on 2007-11-30
> **buck65 said:**
> ```
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
```
Looks like a driver issue.

Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's CODE tag please (# button)

---

### Post by s6long1 on 2007-12-09
im having the same issue...i had Compiz working for months now, but after adding the CPU Frequency Scaling Monitor, Compiz broke (after rebooting)! 

here is what i get when i try compiz --replace:
```
steve@deepthought:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

here is grep -v ^# /etc/X11/xorg.conf:
 ```
steve@deepthought:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection



Section "Extensions"
        Option          "Composite"     "Disable"
        Option          "Composite"     "0"
EndSection

Section "Module"
        Load            "glx"
EndSection

```

why would adding an applet to the gnome bar kill compiz?

-steve
**********************************************
HP dv5000, 512 ram, ATI XPRESS 200M graphics, etc...
[email]extremeconservative@gmail.com[/email]

---

### Post by s6long1 on 2007-12-11
please help!

---

