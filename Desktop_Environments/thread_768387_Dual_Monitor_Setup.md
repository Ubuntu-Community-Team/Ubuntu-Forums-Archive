---
title: "Dual Monitor Setup"
date: 2008-04-26
forum: Desktop Environments
---

### Post by jrdaparker on 2008-04-26
Hi,

I just installed Hardy and everything seemed to go fine, except that I can't both of my monitors to work.

I did a search in the forum and I saw some mention of a "Monitor Menu", but I can't find that.

I changed some of the settings in my xorg file, but that did not seem to help.  Funny thing though, a couple times I think I screwed it up so bad that when I restarted the X server, another application came up, that allowed me to select my monitor, graphics card, etc.  That is probably what I need to use, but I can't seem to bring it up (when I want to).  

I have a Nvidia Geforce 7600GT graphics card and 2 Samsung Syncmaster 204B monitors.  

Any help would be greatly appreciated!

---

### Post by Nythain on 2008-04-26
you could try hitting alt+f2 and typing
gksu nvidia-settings

and making any adjustments there, enabling both monitors, deciding how you want to run dual monitors, and changing thier resolutions and refresh rates... then save.

thats only going to work if you are running the nvidia drivers and not the nv drivers of course, but your only going to get dual monitors with the nvidia drivers as far as i know, at least effectively... so the first thing to do would be make sure you are using nvidia instead of nv by looking in your xorg.conf for the DEVICE entry for your card, and make sure DRIVER reads "nvidia" and not "nv"

outside of the nvidia-settings tool, it gets tricky and complicated to get both monitors working exactly how you want, so i highly advise just sticking with it :)

---

### Post by artir on 2008-04-26
There is a utility to do that in system-preferences-screen resolution

---

### Post by jroes on 2008-04-26
After upgrading to Hardy, nvidia-settings has completely disappeared on my system.

```

jroes@jroes-desktop:~$ sudo find / -name nvidia-settings
jroes@jroes-desktop:~$ 

```

---

### Post by fearpi on 2008-04-26
Then reinstall it.

```
sudo apt-get install nvidia-settings
```

---

### Post by jrdaparker on 2008-04-26
I was able to install nvidia-settings and run that and I was able to create the following xorg.conf file:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
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
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
# 
# removed the comment in front of this line
#    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1600x1200@60 +0+0, DFP-1: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "screen1"
    Device         "Videocard0"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


But my 2nd monitor still won't work.  Does anyone see what is wrong?

---

### Post by jrdaparker on 2008-04-28
I was able to fix the problem!  I did some surfing and found a few links to setting up dual monitors.  The best ones were on the nVidia site.  They explain each of the settings and setting up dual monitors.  Here's the link:

[http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)

Here's a copy of the xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "SyncMaster 204b"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "TwinView"
    Option "MetaModes"   "DFP-0: 1600x1200,  DFP-1: 1600x1200"
    Option "HorizSync"   "DFP-0: 30.0-81.0;  DFP-1: 30.0-81.0"
    Option "SecondMonitorHorizSync"   "30.0 - 81.0"
    Option "SecondMonitorVertRefresh" "56.0 - 75.0"
    Option "TwinViewOrientation"      "RightOf"
    Option "ConnectedMonitor"         "DFP-0, DFP-1"

EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

