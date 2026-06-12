---
title: "compiz fusion with Nvidia FX 400 Not working"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by jonawald on 2007-12-29
Ok I am new to Ubuntu, have been using Linux for a while, I want to get Compiz fusion to work in Ubuntu. Here is the output when I try to run compiz in the terminal. I have tried reading some of the other threads on this topic but there does not seem to be a solution for me. Hopefully somebody with more experience can help me here.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2880x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Segmentation fault (core dumped)
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Sef on 2007-12-29
System > Administration > Restricted Drivers Manager

That will install some proprietary drivers with XGL and with those you should be able to get compiz-fusion working.

---

### Post by jonawald on 2007-12-29
I did that. Long before I got to the point of trying to install Compz.

---

### Post by jonawald on 2007-12-30
> **jonawald said:**
> 
Segmentation fault (core dumped)
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

does this part of the output say that there is a problem other than my computer or hardware not being set up properly?

---

### Post by Forlong on 2007-12-30
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button) instead of the QUOTE tag.

---

### Post by jonawald on 2007-12-30
```
jonathan@UbunTracker:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1        Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3        Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1        Compiz configuration system bindings
jonathan@UbunTracker:~$
```

Ok, that work, never heard of a code tag. Thanks.

---

### Post by Forlong on 2007-12-30
Did you have any other version of Compiz and/or Beryl installed previously?

---

### Post by jonawald on 2007-12-30
Nop, this is a completely new installation of Ubuntu.

---

### Post by Forlong on 2007-12-31
Could you please post your xorg.conf: ```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by jonawald on 2008-01-12
Sorry for the delay, I have been busy, in the mean time, I reinstalled ubuntu, I have done all the updates and tried again. Even with the Nvidia drivers installed, I get the same problem. Here is the code.

```

jonathan@UbunTracker:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "alt-intl"
Option "XkbOptions" "lv3:ralt_switch"
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
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
Identifier "nVidia Corporation NV34 [GeForce FX 5200]"
Boardname "nv"
Busid "PCI:1:0:0"
Driver "nvidia"
Screen 0
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Vendorname "Generic CRT Display"
Modelname "Monitor 1280x1024"
Horizsync 31.5-81.0
Vertrefresh 50-75
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV34 [GeForce FX 5200]"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1600 1200
Modes "1600x1200@65" "1600x1200@60" "1400x1050@60" "1280x960@75" "1280x1024@60" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
screen 1 "screen1" rightof "Default Screen"
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
EndSection
Section "Module"
Load "glx"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "nv"
Busid "PCI:1:0:0"
Driver "nvidia"
Screen 1
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
SubSection "Display"
Depth 24
Modes "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1400x1050@60" "1024x768@75" "1600x1200@65" "832x624@75" "1600x1200@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection
Section "monitor" #
Identifier "monitor1"
Vendorname "Generic CRT Display"
Modelname "Monitor 1280x1024"
Horizsync 31.5-81.0
Vertrefresh 50-75
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
Gamma 1.0
EndSection
Section "ServerFlags"
Option "Xinerama" "true"
EndSection
jonathan@UbunTracker:~$

```

---

### Post by Promaster91 on 2008-01-12
Try this, go to Synaptic Package Manger found in System>Administration>Synaptic Package Manger. Search for compiz. Then "completely remove" compizconfig-settings-manger. Once it removes it reinstall it and it should work. I had the same problem on my computer when I first started.

---

### Post by Forlong on 2008-01-13
I think the problem is with xinerama. Try switching to twinview.

---

### Post by jonawald on 2008-01-13
How do I switch to twinview? How do I edit that xorg.conf file as root? Is there another way to switch to twinview?

---

### Post by Forlong on 2008-01-13
Try this:
```
sudo nvidia-settings
```

---

