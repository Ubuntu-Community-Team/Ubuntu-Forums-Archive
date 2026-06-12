---
title: "Multiple montors = huh?"
date: 2007-11-23
forum: Desktop Environments
---

### Post by moliver on 2007-11-23
I've had Linux for about 2 hours now so talk very slowly to me please...

OK.  I'm running the proprietary nVidia drivers on my Geforce 6600...
I have a 19 inch (1600x1200) and a 17 inch (1280x1024) monitor.
If I tell Ubuntu I want both monitors then I end up having the resolution bigger than the monitor (even though it still says 1600x1200) and I have to do that ANNOYING scroll around the screen thing.  So if I turn off my 17 inch monitor again (ie switch it to disabled) then the 19 inch STILL does the scroll thing (which I hate), but this time when I go to settings it's on some bizare big resolute (17XX x XXXX sorry I can't remember... big anyways).  So I switch it back to 1600x1200 and all is well... except I'm back to one monitor...


Please help :(

---

### Post by superyounan1 on 2007-11-23
There is much information about multi-monitor configurations in the forum, here are some search terms you should find helpful:

xorg.conf - this configuration file is very important in screen configuration. There is also a GUI tool to modify it in ubuntu gutsy, choose System > Administration > Screens and Graphics, or you can access it by pressing Alt+F2 and entering the command "gksu displayconfig-gtk", but often you'll find tutorials on this forum have you edit the xorg.conf file directly, instructions should go along with it.

dual-head - a setup where you have multiple instances of your desktop environment, one on each screen. It would be like having two computers almost in the sense that you can't drag windows from one to the other, but it is nice if you want to have multiple full-screen applications running.

xinerama - a stretched desktop configuration

twinview - i don't have an nvidia card, but i think this is a setting available for their drivers  

also try this link:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn)

if you still can't get this quite right, report back

---

### Post by Linteg on 2007-11-23
Try running nvidias own tool, called "nvidia-settings" and configure the displays with it (Alt-F2, nvidia-settings).

---

### Post by moliver on 2007-11-23
Well I tried the nvidia-settings program and I get the same result.

As for everything else, I don't know enough about Linux to even begin to understand what I should be doing... I'd just heard Ubuntu was easy... I guess I'm going back to Windows :(

---

### Post by Tenken on 2007-11-23
I had a similar problem with my card, and to fix it first I used the nvidia-settings tool to create two separate desktops (can't drag windows) then restarted X (Ctrl+Alt+Backspace) then set it to use Xinerama and restarted X one more time.

Also, make sure you are running the nvidia tool as root or it won't save any of the changes  you made. To do that go to Applications->Accessories->Terminal and type
```
sudo nvidia-settings
```

---

### Post by chronographer on 2007-11-24
Hey mate

Don't give up so easily! Try the gui tools mentioned above, which are pretty good in my opinion, just as good as windows tools. so try:

> pressing Alt+F2 and entering the command "gksu displayconfig-gtk", 
And:
> nvidias own tool, called "nvidia-settings" and configure the displays with it (Alt-F2, nvidia-settings).
And if these can't set it up to your liking, then edit /etc/X11/xorg.conf manually, which is complex but rigorous and very stable, once you have what you like! I use this page to help me set up my dual display with a tv out and lcd:

> [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) Which can be adapted to using two monitors fairly easily, although it may be better to search for nvidia dual displays and find someone's howto with two lcd's

Good Luck, don't give up cause Linux gives good value in the end, and we learn things!

alex

---

### Post by vladk2k on 2007-11-25
I have the exact same problem. I've gone to great lengths to fix it, but I simply can't find any. Posts around the forum seem to revolve on edgy/feisty, where things were diferent (back then, nvidia-settings didn't allow for TwinView, only clone / separate X).

So this is how it goes: Firing up System -> Administration -> Screens and Graphics I change it so that the second monitor extends the first to the right. It says "All users must log off in order for this to have effect" so i restart X (Ctrl + Alt + Backspace), and I'm baffled by the result (you can check it in the screenshot attached"

Some of you may argue that setting primary monitor to 1280x1024 and the secondary to 1280x960 is not good (they should be the same) but I've tried setting the same and the result is the same. I've even tried 1024x768 on both of them.

What happens is (look at the screenshot) the left screen (default) only displays the highlighted area. Moving the mouse past those edges scrolls the image inside the screen. However, moving the mouse further to the right (past the "turn off" button) snaps it into the second screen (which, somehow, doesn't show up in the screenshot - it pastes from the clipboard as transparency, so I've filled it partially with a gradient so that you know something is there) which also scrolls, this time only up and down I think. Dialog boxes can be moved around, all is as expected to work internally, but the display just goes horribly wrong. It should at least have been 2360x1024, not this humongous resolution.

Obs: I see in xorg.conf that the option for Xinerama is turned on when using two displays

So, I disable the second screen, go into nvidia-settings, and sure enough it tells me that the screen is disabled. I enable it, tell it I want "TwinView". Set up the resolutions and whatnot, then I say apply (note, I don't do this with administrator privileges) and nothing happens. So I say yeah, save to xorg.conf and I only preview it, and I see that what it does is create new sections for my video card and both monitors (so now there would be two of each) with the option "TwinView" now set and some metamode that is a hell of a lot longer than it should be, comprising of different positions that there might be (look further down) for the screens. Sometimes it even tells me that it is too long (over 900 characters!!!) and if I want to truncate it or not.

Here it is without truncation:
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#this is my primary monitor

Section "Monitor"
    Identifier     "SyncMaster"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 757DF(X)/707DF(X)/700IFT/CD177A(P)"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

#this is my secondary monitor
Section "Monitor"
 #        
    Identifier     "monitor1"
    VendorName     "Acer"
    ModelName      "Acer 76e"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 110.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

# this is put in by nvidia-settings
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
EndSection

#this is detected by ubuntu
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

#this is put in by nvidia settings
Section "Device"
 #        
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

#this is put in by nvidia-settings - don't know what it does!
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

#this is the default config loaded by ubuntu
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     2048 1536
        Depth       24
        Modes      "1280x1024@85" "1280x1024@60" "1280x960@85" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@43" "1600x1200@60" "1024x768@60" "1600x1200@75" "1024x768@70" "1600x1200@70" "1024x768@75" "1792x1344@60" "1024x768@85" "1856x1392@60" "832x624@75" "1920x1440@60" "800x600@60" "2048x1536@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

#this is the nvidia-settings config
Section "Screen"
 #        
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768@85" "1024x768@75" "832x624@75" "1024x768@70" "800x600@60" "1024x768@60" "800x600@85" "1024x768@43" "800x600@75" "1152x864@75" "800x600@72" "1280x960@60" "800x600@56" "1280x1024@60" "640x480@85" "1400x1050@60" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

#this too - notice the Option TwinView 1 tag 5 lines below
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024@85 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x1024@60 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960@85 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960@75 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960@60 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x1024@75 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1152x864@75 +0+0, CRT-1: nvidia-auto-select +1152+0; CRT-0: 1024x768@43 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 1024x768@60 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 1024x768@70 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 1024x768@75 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 1024x768@85 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624@75 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600@60 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 800x600@85 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 800x600@75 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 800x600@72 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 800x600@56 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480@85 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 640x480@75 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 640x480@72 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 640x480@60 +0+0, CRT-1: nvidia-auto-select +640+0"
EndSection

## Usually there is a thing here with Xinerama 1 when configuring by "Screens and graphics"


Anyone know what do I have to do?

---

### Post by vladk2k on 2007-11-25
Ok, after trying absolutely EVERY scenario which came to mind, I've finally made it work (yay for me!)

After messing my config to the point that Both monitors entered standby, I've reverted to the default configuration, by running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and then, after restarting the system (or restarting X) the driver was the old one ("nv").
I then went to System -> Administration -> Restricted Drivers Management and activated the Nvidia driver. I had to restart the system.

Now, for the most important part. **Without** going to Screens and Graphics, I pressed Alt+F2 (Run command) and entered ```
gksu nvidia-settings
``` On the second option from the left list I chose the second screen, Config -> TwinView, put whatever resolution I wanted and pressed "Save to X configuration file". Then. Ctrl + Alt + Backspace and voila!

Well, first I got something like 640x480 on both screens (but it worked as intended!) - quick pace to System -> Preferences -> Screen resolution -> 2560x1024 (I set both monitors to 1280x1024) and there it was.

Afterwards, I played a little and now I have 1280x1024 on the first monitor and 1024x768 on the second, both running at 85Hz (I can't stand 60Hz, makes me want to scratch the inside of my eyes)

Here is my new /etc/X11/xorg.conf
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:5:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 720x400 +0+0, CRT-1: nvidia-auto-select +720+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024_85 +0+0, CRT-1: 1024x768_85 +1280+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 720x400 +0+0, CRT-1: nvidia-auto-select +720+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
EndSection


Note to **moliver**
Even if ubuntu seems pretty user friendly, it's not that easy to configure as with windows. Every configuration is kept in a file, most of these you will find in /etc folder. To edit them, you need special privileges (root) so that somebody coming to your turned on computer cannot mess them. To do that, you have three choices:
[LIST]
[*]sudo - which runs the immediate afterward command as root - works for console programs
[*]gksu - which runs the immediate after command as root but is intended for graphical programs, such as gedit
[*]sudo su - which turns the console into root privileges - meaning you can run anything without needing to put sudo in front
[/LIST]
I know, in Windows you are administrator and can configure anything. Here it's a little more complicated, but you can always trust that it's a bit safer (if someone comes to your computer and deletes the Windows folder, you can't stop them. If they try to do the same to the /etc folder or the /usr folder... it doesn't work.
Another good thing about having configuration files rather than keeping them hidden in a registry that you cannot access normally, is that you can access them from the terminal if the graphical interface doesn't wok anymore. Or from a remote ssh connection. There is much digging to be done. I've been using ubuntu for a year now and still I'm a beginner at most things

---

