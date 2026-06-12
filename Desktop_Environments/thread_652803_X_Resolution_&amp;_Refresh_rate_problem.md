---
title: "X Resolution &amp; Refresh rate problem"
date: 2007-12-29
forum: Desktop Environments
---

### Post by pawel_dyda on 2007-12-29
Hi,

I have tried everything (googling hard), but I have no idea what's going on.
I've got IIyama Vision Master 514 (HM204DT A) on GeForce 6600 Top. I would like to set up screen resolution to 1280x1024 with at **least** 120Hz refresh rate. Well, it is not so easy I suppose. Although I have correct modes in my xorg.conf (see bellow), both displaysettings and nvidia-settings ignores them and I can only set at most 85Hz refresh rate (funny thing - displaysettings claims that this is 128Hz :>). I was able to set it up correctly ones (yesterday), but of course it would be just to easy if these settings persist. Any magic commands, configuration files,  ideas? Thanks.

xorg.conf 
<snip>
Section "Monitor"
    Identifier     "HM204DA/DTA"
    VendorName     "IIYAMA"
    ModelName      "HM204DTA"
    HorizSync       30.0 - 142.0
    VertRefresh     50.0 - 200.0
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
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@133" 261.2 1280 1384 1528 1776 1024 1025 1028 1106 -hsync +vsync
    ModeLine       "1280x1024@130" 254.9 1280 1384 1528 1776 1024 1025 1028 1104 -hsync +vsync
    ModeLine       "1280x1024@120" 233.8 1280 1384 1528 1776 1024 1025 1028 1097 -hsync +vsync
    ModeLine       "1280x1024@110" 211.2 1280 1376 1520 1760 1024 1025 1028 1091 -hsync +vsync
    ModeLine       "1280x1024@100" 191.0 1280 1376 1520 1760 1024 1025 1028 1085 -hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
    ModeLine       "1920x1440@85" 341.4 1920 2072 2288 2656 1440 1441 1444 1512 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
    ModeLine       "2048x1536@85" 388.0 2048 2216 2440 2832 1536 1537 1540 1612 -hsync +vsync
    ModeLine       "2048x1536@75" 340.5 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
EndSection
</snip>

---

### Post by pawel_dyda on 2007-12-29
It seems like I haven't give enough details:

Kubuntu 7.10 (Gutsy), restricted binary nvidia driver, AMD64.

It seems that xorg is ignoring the section I mentioned in previous post. It has re-detected (sic!) monitor and create another section. I have copy over some modes to it, killed X and then I can choose 120Hz refresh rate in nvidia-settings. Now, what can I do to make these settings persistent? I don't to go through that all over again... Is there any way to **force** refresh rate? Thanks.

New section:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Iiyama HM204DA/DTA"
    HorizSync       30.0 - 142.0
    VertRefresh     50.0 - 200.0
    ModeLine       "1280x1024@133" 261.2 1280 1384 1528 1776 1024 1025 1028 1106 -hsync +vsync
    ModeLine       "1280x1024@130" 254.9 1280 1384 1528 1776 1024 1025 1028 1104 -hsync +vsync
    ModeLine       "1280x1024@120" 233.8 1280 1384 1528 1776 1024 1025 1028 1097 -hsync +vsync
    ModeLine       "1280x1024@110" 211.2 1280 1376 1520 1760 1024 1025 1028 1091 -hsync +vsync
    ModeLine       "1280x1024@100" 191.0 1280 1376 1520 1760 1024 1025 1028 1085 -hsync +vsync
EndSection

---

### Post by pawel_dyda on 2007-12-30
Re,

Nobody answered, so I have to do it myselft (was it to simple or to hard?).

Well, I don't know how to force refresh rate. All I know, I had to add ModeLines presented above to Monitor section in xorg.conf (the one that was detected by xorg server, do not modify vendor string, as it will be detected again, I don't know why and I don't want to guess; it seems like some kind of a bug). Then I have to use:
*sudo nvidia-settings*
and set the display mode and refresh rate as desired. It will be kept untill reboot. To avoid changing these settings during KDE start, one should go to /etc/X11/Xsession.d/ and edit 40guidance-displayconfig_restore startup script. I have commented line that goes like this:
/usr/bin/displayconfig-restore || true
and now it seems like Kubuntu is not trying to be wiser than me. Now, nvidia-settings reports correct resolution and refresh rate. However, diplayconfig shows 1280x1024@50 :>  displayconfig issue, I guess.

Hello for anyone who will google it up :)

---

### Post by s6dalane on 2008-03-08
I have the same problem, but I do not have the file mentioned in the last post. Gnome-display-properties do not work and when I change the settings with displayconfig-gtk, my xorg.conf is resetted after reboot.

---

