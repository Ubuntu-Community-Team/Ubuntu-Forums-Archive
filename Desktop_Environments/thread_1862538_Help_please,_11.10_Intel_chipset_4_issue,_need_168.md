---
title: "Help please, 11.10 Intel chipset 4 issue, need 1680x1050"
date: 2011-10-16
forum: Desktop Environments
---

### Post by branislavski on 2011-10-16
Sony vaio vgc-js320j reading two monitors falsely

Xrandr output:

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
1024x768 60.0 
800x600 60.3 56.2 
848x480 60.0 
640x480 59.9 
vaio 60.0 
LVDS1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1600x1200 60.0*+
1600x1024 60.2 
1400x1050 60.0 
1280x1024 60.0 
1440x900 59.9 
1280x960 60.0 
1360x768 59.8 60.0 
1152x864 60.0 
1024x768 60.0 
800x600 60.3 56.2 
640x480 59.9 
CUSTOM (0xc9) 147.1MHz
h: width 1680 start 1784 end 1968 total 2256 skew 0 clock 65.2KHz
v: height 1050 start 1051 end 1054 total 1087 clock 60.0Hz
1680x1050_60.00 (0xcb) 147.1MHz
h: width 1680 start 1784 end 1968 total 2256 skew 0 clock 65.2KHz
v: height 1050 start 1051 end 1054 total 1087 clock 60.0Hz


LVDS1 resolution is the monitor thats says LAPTOP (i have a desktop) and the VGA1 is listed as unknown in my display settings.

i tried to add resolution using xrandr to lvds1 but failed

here is the output:

branislav@ubuntu:~$ xrandr --addmode LVDS1 1680x1050_60.00
X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 150 (RANDR)
Minor opcode of failed request: 18 (RRAddOutputMode)
Serial number of failed request: 25
Current serial number in output stream: 26

Please help to make desktop realize i have only one monitor or at least to set lvds1 to 1680x1050.

---

### Post by branislavski on 2011-10-18
bump.......

---

