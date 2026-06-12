---
title: "Lubuntu 18.04 HDMI TV Setup"
date: 2019-02-28
forum: Desktop Environments
---

### Post by spode2 on 2019-02-28
I am using an Intel NUC with a HDTV, but the video display quality is poor and, with no proprietary driver, there does not seem to be an easy way to adjust contrast, brightness, and colour.

From what I have read, xorg.conf is not used now, and the EDID is somehow used to select one of the preconfigured files in /usr/share/X11/xorg.conf.d/

The monitor setting in Lubuntu is correct at 1280x1024, 60Hz but the output of get-edid does not make sense to me. 

~$ sudo get-edid | parse-edid

Section "Monitor"
    Identifier "LG TV"
    ModelName "LG TV"
    VendorName "GSM"
    # Monitor Manufactured week 1 of 2014
    # EDID version 1.3
    # Digital Display
    DisplaySize 1600 900
    Gamma 2.20
    Option "DPMS" "false"
    Horizsync 30-83
    VertRefresh 58-62
    # Maximum pixel clock is 160MHz
    #Not giving standard mode: 640x480, 60Hz
    #Not giving standard mode: 800x600, 60Hz
    #Not giving standard mode: 1024x768, 60Hz
    #Not giving standard mode: 1152x864, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz

    #Extension block found. Parsing...
    Modeline     "Mode 16" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 85.50 1360 1424 1536 1792 768 771 777 795 +hsync +vsync 
    Modeline     "Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 3" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 4" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 5" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 6" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 7" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
    Modeline     "Mode 8" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 9" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 10" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 11" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 12" 74.250 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 13" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 14" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 15" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Modeline     "Mode 17" 74.25 1280 1390 1526 1664 720 725 730 746 +hsync -vsync 
    Modeline     "Mode 18" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 19" 85.50 1360 1424 1536 1792 768 771 777 795 +hsync +vsync 
    Option "PreferredMode" "Mode 16"
EndSection

I would be grateful if someone can tell me what I need to do to get a good quality HD display on the screen. Better still, is there a GUI for doing this?

---

### Post by Autodave on 2019-02-28
What kind of cable are you using to connect the NUC to the TV?

---

### Post by CatKiller on 2019-02-28
> **spode2 said:**
> From what I have read, xorg.conf is not used now, and the EDID is somehow used to select one of the preconfigured files in /usr/share/X11/xorg.conf.d/

No. xorg.conf *is* used, if it's there. It is not there by default. You can also use snippets of the configuration as files in xorg.conf.d rather than having everything in a single xorg.conf file. They are all applied, if they can be. 

Rather than specifying everything in a rigid configuration, EDID allows the monitor to tell the computer which resolutions and timings it uses. 

> The monitor setting in Lubuntu is correct at 1280x1024, 60Hz 

1280×1024 is not a television resolution. It is a weird resolution that was only used for monitors. If you're using a television it will have a resolution of either 1280×720 or 1920×1080.

---

