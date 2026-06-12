---
title: "Dual monitors, full screen, Lenovo T61P with gutsy"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by leenooks on 2007-11-05
I'm stuck on a dual screen problem, and dont know where to google for help. Some pointers would be great.

I have a T61P (nVidia Corporation Quadro FX 570M (rev a1)) - which when I installed Gutsy and tried the "Screens and Graphics" to enable an external monitor, it just didnt work. "Test" was greyed out, and "OK" after setting the 2nd monitor as "mirror" of the main screen did nothing.

So I played around with xorg.conf, and got a dual screen config working - it works well except for my problem below...

* When there is nothing plugged into the VGA port, I get 3D desktop (cube and all), at 1920 x 1200 - no problems.

* When an external monitor is plugged into my VGA port, I need to restart X (or logoff if I was logged in), and X probes the screen resolution of my external device and display to it.

On the LCD display, the login screen takes up the right hand corner, not taking up the full screen, but taking up the size of the external monitor (eg: 800x600 or 1024x768). The LCD screen is still at 1920 x 1200 though (the reset of the space is the X background colour). On the external monitor, its "full screen". This is actually no problem.

Some ASCII art to describe what I see on the LCD:

```
+-----+-------+
| EXT |       |
+-----+       |
|             |
| LCD         |
+-------------+
```

Thus, my external monitor only shows the content in the "EXT" space, where my LCD is sized at 1920x1200, and looks like the ASCII art.

When I login, my top and bottom panels are perfect on the external monitor (ie: at the top and bottom of the display). My panels on the LCD though are shown as taking up a screen size, as per the ASCII art above - taking up the boundary of the "EXT" box. This the top panel goes from the top left hand corner to the top middle of the LCD display. The bottom panel goes from the middle left of the screen in a horizontal line to the middle of the screen.

So, if I start any X application, if I move the X app into the top right hand corner (the "EXT" area), it is seen on the external monitor, if the X app is outside the "EXT" above it is seen on the LCD only. This is no problem either.

If I use "rdesktop" with "fullscreen", then the external monitor shows the correct full screen - and it only occupies the "EXT" portion of my display when looking at the LCD. (This is great.)

If I start OpenOffice Impress, and select "Slide Show", it unfortunately takes up my "LCD" full screen, not the "EXT" full screen, and thus the external monitor only shows the portion of the slide show, occupying the "EXT" part of the screen. (IE: 1/4 of of it)

How can I make OpenOffice full screen only take up full screen in the "EXT" part as rdesktop does?

Here is my xorg.conf if that helps?
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Screen          0
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "TwinView"      "on"
        Option          "TwinViewOrientation"   "clone"
        Option          "SecondMonitorHorizSync"        "30-83"
        Option          "SecondMonitorVertRefresh"      "55-85"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        
        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Disable         "dbe"
        Disable         "dri"
        Disable         "glx"
        Disable         "vbe"
        Load            "glx"
        Load            "v4l"
EndSection
#--
Section "Device"  
        Identifier      "VGA Video"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen          1
        Option          "TwinView"      "on"
        Option          "TwinViewOrientation"   "clone"
        Option          "SecondMonitorHorizSync"        "30-83"
        Option          "SecondMonitorVertRefresh"      "55-85"
EndSection
Section "Screen"
        Identifier      "VGA Screen"
        Device          "VGA Video"
        Defaultdepth    24
        Monitor         "VGA Monitor"
EndSection

Section "Monitor" #  
        Identifier      "VGA Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
        Gamma   1.0
EndSection

```

---

### Post by garythornton1956 on 2007-12-07
I cannot help you with a solution but I can share your pain.  I have the same setup and get the same problem, so it is not unique to you.

I've tried everything I know to solve it, but without success.  However, my knowledge is good but not expert.   I suspect it may be to do with the links between Gutsy and the NVIDIA proprietary drivers but you have to use those to get the screen resolution to work properly.

As I am a recent 'convert' from Mandriva I am tempted to install Mandriva 2008 and see if I get the same situation there.  I don't really want to though.

---

### Post by McLogic on 2007-12-12
> **garythornton1956 said:**
> I cannot help you with a solution but I can share your pain.  I have the same setup and get the same problem, so it is not unique to you.

I bought a T61p and it has had 3 problems: **Network Manger** hangs after suspend/hibernate, **no suspend/hibernate** with Nvidia drivers, USB ports on the right side (2 of the computer's 3) do not work after boot sequence (but do work during).

> **garythornton1956 said:**
> I've tried everything I know to solve it, but without success.  However, my knowledge is good but not expert.   I suspect it may be to do with the links between Gutsy and the NVIDIA proprietary drivers but you have to use those to get the screen resolution to work properly.

[SIZE="4"]**We all need to get nVidia to open their drivers. This blob stuff is BS.**[/SIZE]

[[SIZE="5"][COLOR="RoyalBlue"]http://new.petitiononline.com/nvfoss/petition.html[/COLOR][/SIZE]]("http://new.petitiononline.com/nvfoss/petition.html")

> **garythornton1956 said:**
> As I am a recent 'convert' from Mandriva I am tempted to install Mandriva 2008 and see if I get the same situation there.  I don't really want to though.

You can go with **VESA driver**, but you will get no 3d and choppy video (about 15 fps). I would rather use VESA then be stuck with old-French Red Hat again.

[http://ubuntuforums.org/showpost.php?p=3800803&postcount=4](http://ubuntuforums.org/showpost.php?p=3800803&postcount=4)

---

### Post by cugase2 on 2008-06-22
did you found a solution of the dual screen lenovo t61p problem? Also other hints in running this notebook perfectly under Linux are very welcome! 
Cheers

---

