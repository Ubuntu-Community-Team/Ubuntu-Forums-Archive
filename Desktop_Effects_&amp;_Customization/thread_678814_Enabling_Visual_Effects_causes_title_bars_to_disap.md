---
title: "Enabling Visual Effects causes title bars to disappear"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by akudewan on 2008-01-26
I did a fresh install of Ubuntu Gutsy, and installed the nvidia restricted drivers. That was successful. However, when I try to enable Visual Effects from System > Preferences > Appearance, the title bar of all the windows disappears.

The other effects seem to work fine, only the title bars disappear. Can anyone help me fix this?

---

### Post by alxlabs on 2008-01-26
I just experienced very similar thing - I had visual effects enabled, everything seemed to work fine. Then (i don't know why) I decided to change screen refresh rate. Nothing changed but title bar disappeared if visual effects are enabled. Bar goes back once I disable them and disappears if I enable. I reverted to my previous xorg.config - everything went back to normal, so there is something wrong with it. I newbie to linux&ubuntu so I dont know what exactly went wrong but I hope it will help you if I attach both xorg.confs , working and not-working

---

### Post by rhc on 2008-01-26
While desktop affects on,
Try > metacity --replace.Then > compiz --replace again.
If the same thing appears,then try > emerald --replace

---

### Post by BuntuFreak on 2008-01-26
Finally, more and more reporting the problems I'm facing as well !!!

Okay I want to try the "replace" suggestion. Problem is when I enable desktop effects, i.e. enable compiz, any terminal session I start stops posting characters. So I can't see what I'm doing.

Any ideas how I can fix my blank Terminal problem. Sans window decorations I can live with, Terminal going blank is just unacceptable. Much as I'm love Ubuntu, this will force me to go back to Vista :(

---

### Post by BuntuFreak on 2008-01-26
Finally, some Compiz / Emerald errors I can post after doing the "replace" options suggested. Please look at the attached error file. Maybe it tells you something. Needless to say I'm totally lost.

---

### Post by chronic on 2008-01-26
> **BuntuFreak said:**
> Finally, some Compiz / Emerald errors I can post after doing the "replace" options suggested. Please look at the attached error file. Maybe it tells you something. Needless to say I'm totally lost.

please post your xorg.conf file

---

### Post by rosegarden78 on 2008-01-26
Try pressing Alt-F2 and type "compiz" to reload.  Make sure you have all packages named "compiz" from Synaptic as well as Ubuntu GG 7.10.  Or try [these]("http://ubuntuforums.org/showthread.php?t=677959") [links]("http://ubuntuforums.org/showthread.php?t=385981").

---

### Post by BuntuFreak on 2008-01-26
My problem is almost solved. I had to enable nvidia card for compiz as posted on another thread.

Now if only I can get the cube faces and caps to use the image I'm specifying...

---

### Post by akudewan on 2008-01-27
Hi,

Thanks for the replies.

@rhc: when I try metacity --replace, the effects get turned off, and the title bars reappear. So thats no use.
compiz --replace does nothing, and the emerald command does not exist.

I started compiz from the terminal, and got this output:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0171 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

```

This is my /etc/X11/xorg.conf
```

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
        Identifier      "nVidia Corporation NV17 [GeForce4 MX 440]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1440x900@75"   "1440x900@60"   "1280x800@60"   "1600x1024@60"  "1280x768@75"   "1680x1050@60"  "1280x800@75"   "1680x1050@75"  "1280x720@60"   "1920x1200@60"   "1280x768@60"   "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by akudewan on 2008-01-29
Hello, does anyone remember me? I was the one who started this thread...

---

### Post by akudewan on 2008-01-29
Ok, I dug around a bit, and decided to install xserver-xgl. That solved the problem.

However, things were moving too slow, so I decided to disable it...

---

### Post by chronic on 2008-01-31
you dont need xgl 

just type this in terminal 

sudo apt-get install emerald

then enable compiz when you have no title bar hit alt+f2 then type emerald --replace

---

### Post by akudewan on 2008-02-02
> **chronic said:**
> you dont need xgl 

just type this in terminal 

sudo apt-get install emerald

then enable compiz when you have no title bar hit alt+f2 then type emerald --replace

That also didn't work. emerald --replace gives no o/p in the terminal, and the window decorations are still missing

---

### Post by akudewan on 2008-02-02
I did some more digging, and found [this page]("http://linuxevangelist.blogspot.com/2007/06/ubuntu-7-no-window-borders-on-desktop.html").

Simply had to add the line **Option "AddARGBGLXVisuals" "True"** in the screens section of the xorg.conf file. Everything works now, and its a LOT faster than xgl enabled.

Thanks for the help everyone :)

---

### Post by trashmonkey on 2008-04-27
Adding in Option	   "AddARGBVisuals"	"True" and Option	   "AddARGBGLXVisuals"	"True" in the Section "Device" to the /etc/X11/xorg.conf fixed mine!!!  :) I've been trying to fix this for days!  Now I can really start playing around with making my desktop look awesome!  Here's what my whole device section looks like:

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4400"
    Option	   "AddARGBVisuals"	"True"
    Option	   "AddARGBGLXVisuals"	"True"
    Option	   "NoLogo"	"True"
EndSection

---

### Post by shinkaide on 2008-04-30
Wow, thanks a lot guys. The xorg.conf edit fixed everything. There's a small problem I've got though...

Out of the box, Hardy only has 2 virtual desktops enabled, right? So after doing the fix, I tried adding more desktops by right-clicking on the Workspace Switcher on the lower-right part of my taskbar. I upped the columns to 4 (From 2) and closed it.

Nothing happened. I still have only 2 virtual desktops.

Anybody else experience the same thing after doing the xorg.conf edit?

---

### Post by akudewan on 2008-04-30
> **shinkaide said:**
> Wow, thanks a lot guys. The xorg.conf edit fixed everything. There's a small problem I've got though...

Out of the box, Hardy only has 2 virtual desktops enabled, right? So after doing the fix, I tried adding more desktops by right-clicking on the Workspace Switcher on the lower-right part of my taskbar. I upped the columns to 4 (From 2) and closed it.

Nothing happened. I still have only 2 virtual desktops.

Anybody else experience the same thing after doing the xorg.conf edit?

If you have ccsm installed, run it and go to General Options > Desktop Size.
Try changing the "Horizontal virtual size" to add more workspaces horizontally. That's how I did it...

---

