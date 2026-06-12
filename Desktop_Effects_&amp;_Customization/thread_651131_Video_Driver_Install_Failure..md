---
title: "Video Driver Install Failure."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by thorosius on 2007-12-27
Hy!

So I have an Intel (R) 82852/82855 GM/GME Graphics Controller and I found its driver from Intel's Website. It was mentioned there that the driver works for SuSE and Fedora but I downloaded it anyway, tried to install and (as expected) install failed. A log file was generated. 

Can anyone help me with this? or has anyone seen any help regarding this driver on the web?

dri.log:
```
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/fahd/soft/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/fahd/soft/dripkg/agpgart-2.0/backend.o
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:110: error: previous declaration of ‘agp_backend_acquire’ was here
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:110: error: previous declaration of ‘agp_backend_acquire’ was here
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:111: error: previous declaration of ‘agp_backend_release’ was here
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:111: error: previous declaration of ‘agp_backend_release’ was here
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/fahd/soft/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:281: warning: implicit declaration of function ‘inter_module_register’
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/fahd/soft/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/fahd/soft/dripkg/agpgart-2.0/backend.c:301: warning: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/fahd/soft/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/fahd/soft/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/fahd/soft/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.22-14-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
rm: cannot remove `/home/fahd/soft/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/fahd/soft/dripkg/drm'
make: *** [gdg.ko] Error 2
```

---

### Post by Forlong on 2007-12-27
Since intel's graphics drivers are open source, they are shipped by default in Ubuntu. You don't have to install anything.

---

### Post by thorosius on 2007-12-27
Yes I did see it in the documentation but I am unable to run Compiz-Fusion. So looking at many posts in the forums I suppose I have to install them. Is that right?

---

### Post by Forlong on 2007-12-27
What's the output of ```
compiz
``` in a terminal?

---

### Post by thorosius on 2007-12-27
[SIZE=2]This was the output:[/SIZE]
 
```
 
fahd@fahd-laptop:~$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```
 
 
[SIZE=2]So I downloaded the xserver-xgl, installed it, logged off, logged in again and there was notification message saying that whenever I am going to log in again XGL will start automatically (or something similar). But the output of Compiz in the terminal hasn't changed.[/SIZE]

---

### Post by Forlong on 2007-12-27
First of all: you don't need Xgl with an intel chip, remove it again:
```
sudo apt-get remove xserver-xgl
```

Then post the output of  ```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by thorosius on 2007-12-27
```
 
fahd@fahd-laptop:~$ grep -v ^# /etc/X11/xorg.conf
Section "Files"
EndSection
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

```

---

### Post by Forlong on 2007-12-27
You are using the vesa driver right now. Try changing this
```
Section "Device"
        Identifier     "Generic Video Card"
        Driver         "vesa"
        BusID          "PCI:0:2:0"
EndSection
```
to
```
Section "Device"
        Identifier     "Generic Video Card"
        Driver         "i810"
        BusID          "PCI:0:2:0"
EndSection
```
You have to be root to save the file, so open it like this:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by thorosius on 2007-12-27
Hye it worked! I've installed compiz settings manager and all the effects are running. Thanks!

---

### Post by oamster on 2008-01-10
My friend is having a problem with is drivers, and he too has intel chipset, but when I told him to run "grep -v ^# /etc/X11/xorg.conf" in terminal his video card said:

> EndSection



Section "Device"

        Identifier      "Failsafe Device"

        Boardname       "vesa"

        Busid           "PCI:0:2:0"

        Driver          "intel"

        Screen  0

EndSection

Should I tell him to do edit the xorg.conf like you told the OP?

---

### Post by Forlong on 2008-01-10
oamster, tell your friend to run this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by oamster on 2008-01-10
This is output of the xorg.conf:

>    1.
      kevin@Ninja:~$ grep -v ^# /etc/X11/xorg.conf
   2.
      Section "Files"
   3.
      EndSection
   4.
       
   5.
      Section "Module"
   6.
              Load            "glx"
   7.
              Load            "GLcore"
   8.
              Load            "v4l"
   9.
      EndSection
  10.
       
  11.
      Section "InputDevice"
  12.
              Identifier      "Generic Keyboard"
  13.
              Driver          "kbd"
  14.
              Option          "CoreKeyboard"
  15.
              Option          "XkbRules"      "xorg"
  16.
              Option          "XkbModel"      "pc105"
  17.
              Option          "XkbLayout"     "us"
  18.
      EndSection
  19.
       
  20.
      Section "InputDevice"
  21.
              Identifier      "Configured Mouse"
  22.
              Driver          "mouse"
  23.
              Option          "CorePointer"
  24.
              Option          "Device"        "/dev/input/mice"
  25.
              Option          "Protocol"      "ImPS/2"
  26.
              Option          "ZAxisMapping"  "4 5"
  27.
              Option          "Emulate3Buttons"       "true"
  28.
      EndSection
  29.
       
  30.
      Section "Device"
  31.
              Identifier      "Failsafe Device"
  32.
              Boardname       "vesa"
  33.
              Busid           "PCI:0:2:0"
  34.
              Driver          "intel"
  35.
              Screen  0
  36.
      EndSection
  37.
       
  38.
      Section "Monitor"
  39.
              Identifier      "Failsafe Monitor"
  40.
              Vendorname      "Plug 'n' Play"
  41.
              Modelname       "Plug 'n' Play"
  42.
        modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  43.
        modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  44.
        modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  45.
        modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  46.
        modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  47.
        modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  48.
        modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  49.
        modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  50.
        modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  51.
        modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  52.
        modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  53.
        modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  54.
        modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  55.
        modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  56.
        modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  57.
        modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  58.
        modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  59.
        modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  60.
        modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  61.
              Gamma   1.0
  62.
      EndSection
  63.
       
  64.
      Section "Screen"
  65.
              Identifier      "Default Screen"
  66.
              Device          "Failsafe Device"
  67.
              Monitor         "Failsafe Monitor"
  68.
              Defaultdepth    24
  69.
              SubSection "Display"
  70.
                      Depth   24
  71.
                      Virtual 1600    1200
  72.
                      Modes           "800x600@72"    "800x600@75"    "800x600@56"   "800x600@60"     "640x480@75"    "832x624@75"    "640x480@72"    "1024x768@75"  "640x480@60"     "1024x768@70"   "1024x768@60"   "1152x864@75"   "1280x1024@75" "1280x960@60"    "1280x1024@60"  "1280x960@75"   "1400x1050@60"  "1600x1200@65" "1600x1200@60"
  73.
              EndSubSection
  74.
      EndSection
  75.
       
  76.
      Section "ServerLayout"
  77.
              Identifier      "Default Layout"
  78.
        screen 0 "Default Screen" 0 0
  79.
              Inputdevice     "Generic Keyboard"
  80.
              Inputdevice     "Configured Mouse"
  81.
      EndSection
  82.
      Section "ServerFlags"
  83.
      EndSection
  84.
      kevin@Ninja:~$

---

### Post by oamster on 2008-01-10
Which one should he choose?

> #
 &#9474; For the X Window System graphical user interface to operate correctly,    &#9474;  
#
 &#9474; it is necessary to select a video card driver for the X server.           &#9474;  
#
 &#9474;                                                                           &#9474;  
#
 &#9474; Drivers are typically named for the video card or chipset manufacturer,   &#9474;  
#
 &#9474; or for a specific model or family of chipsets.                            &#9474;  
#
 &#9474;                                                                           &#9474;  
#
 &#9474; X server driver:                                                          &#9474;  
#
 &#9474;                                                                           &#9474;  
#
 &#9474;                              glint            &#8593;                           &#9474;  
#
 &#9474;                              i128             &#9618;                           &#9474;  
#
 &#9474;                              i740             &#9646;                           &#9474;  
#
 &#9474;                              i810             &#9618;                           &#9474;  
#
 &#9474;                              imstt            &#9618;                           &#9474;  
#
 &#9474;                              intel            &#8595;                           &#9474;  
#
 &#9474;                                                                           &#9474;  
#
 &#9474;                                                                           &#9474;  
#
 &#9474;                                  <Ok>                                     &#9474;

---

### Post by Forlong on 2008-01-10
Depends on the chipset but I recommend trying i810

---

### Post by oamster on 2008-01-10
> **Forlong said:**
> Depends on the chipset but I recommend trying i810

Alright I told him to choose the i810 driver, but it's asking to model of the card. Which his is Intel® Graphics Media Accelerator 950. 

Sorry to bother you, I just don't know a whole lot about intel chipsets.

---

### Post by oamster on 2008-01-10
> **oamster said:**
> Alright I told him to choose the i810 driver, but it's asking to model of the card. Which his is Intel® Graphics Media Accelerator 950. 

Sorry to bother you, I just don't know a whole lot about intel chipsets.

Should I tell him to put Intel i950?
Or i810?

---

### Post by Forlong on 2008-01-10
Frankly, I don't have any experience with intel chips either.

Try i950

---

### Post by oamster on 2008-01-10
> **Forlong said:**
> Frankly, I don't have any experience with intel chips either.

Try i950

It's asking to setup the keyboard, and the mouse. Me personally have no idea what mouse and keyboard he has... Does the setup even matter?

---

### Post by Forlong on 2008-01-10
You can safely skip those settings by hitting enter.

---

### Post by oamster on 2008-01-10
Thanks man, we just installed compiz without xgl and everything is running pretty smooth. The problem we were having was when he moved a window it would use 90-100% cpu usage and that was with xgl, so I take it xgl was messing his intel chip up.

---

### Post by PmDematagoda on 2008-01-10
Scratch that. I made a silly mistake.

---

### Post by Forlong on 2008-01-10
> **oamster said:**
> Thanks man, we just installed compiz without xgl and everything is running pretty smooth. The problem we were having was when he moved a window it would use 90-100% cpu usage and that was with xgl, so I take it xgl was messing his intel chip up.
Yup, Xgl can be pretty buggy and it's fortunately not needed with intel chips, because their drivers are open source. :)

---

### Post by DouglasCaixeta on 2008-05-14
Hi,

I'm having the same problem.
But when I write on terminal

```
sudo gedit /etc/X11/xorg.conf
```

The output is:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```


Where I gona change vesa to i810?

---

### Post by Forlong on 2008-05-15
> **DouglasCaixeta said:**
> I'm having the same problem.
What makes you think so?

Could you please elaborate on what your problem is, exactly?
And please give us more information about your system.
You can use [this script]("http://forlong.blogage.de/article/pages/Compiz-Check") for that, if you like.

---

### Post by DouglasCaixeta on 2008-05-15
Hi Forlong,

	
I think I have the same problem because when I shutdown the computer it does not shut off. Appears a black screen and not off.

Here is the output:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Thanks!

---

### Post by Forlong on 2008-05-15
As you can see in the output, the driver is perfectly installed and everything's set up properly.

As for your shutdown problem: I'd start a new thread for that in the "General Help" section -- I do not think it's a driver issue.

---

