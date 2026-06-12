---
title: "something wrong with ati driver"
date: 2005-03-11
forum: Desktop Environments
---

### Post by T31 on 2005-03-11
i have installed the new ati drivers and now something happens, when i use the combination ctrl+alt+"+" the size oxf the desktop grows up but not the size of the screen, i mean the screen displays 800x600 but the size of the desktop grows up to 1024x768  [-o< 

this is my monitor section

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 60.0
    VertRefresh 50 - 70
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection

---

### Post by jrasmussen0 on 2005-03-11
That is correct behavior.  Are you trying to change the size of your monitor?

---

### Post by T31 on 2005-03-11
Im sorry i dont get you my problem is, the resolution changes but doesnt fix to my 14" screen and i lost part of the desktop, i only can see 800x600 from that 1024x768 desktop, something really really bizarre   #-o

---

### Post by sharke on 2005-03-11
i have installed the new ati drivers and now something happens, when i use the combination ctrl+alt+"+" the size oxf the desktop grows up but not the size of the screen, i mean the screen displays 800x600 but the size of the desktop grows up to 1024x768 [-o<

I think you mean when you switch to res above 800x600 you get a virtual screen.
Thiis is when part of the display is of the monitor you can scroll to see the hidden display, Is this the problem you Have

Regards Sharkee

---

### Post by T31 on 2005-03-11
:oops:  O:)  the fault is even worst!

i didnt restart the x-session, now after reboot everything is ok.

 :oops:

hehe too used to dont have to reboot,not even the X :grin:

---

