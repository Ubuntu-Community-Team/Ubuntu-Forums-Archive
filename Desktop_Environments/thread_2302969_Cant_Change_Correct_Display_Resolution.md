---
title: "Cant Change Correct Display Resolution"
date: 2015-11-15
forum: Desktop Environments
---

### Post by mma-95 on 2015-11-15
Hi,

I am using Xubuntu 15.10 and my monitor is BenQ FP222WH. I installed lastest graphic drivers from additional drivers in settings. My graphics card is also GTX 770.

My monitor display is 1680x1050 but i cant see that option in setting. Also there are no other 16:10 displays in the list. I searched in internet and i found these codes but it cant work.

```
maydin@maydin-desktop:~/Desktop$ sudo cvt 1680 1050
[sudo] password for maydin: 
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
maydin@maydin-desktop:~/Desktop$ sudo xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
maydin@maydin-desktop:~/Desktop$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 473mm x 297mm
   1280x720      60.00*+  60.00    59.94    50.00  
   1920x1080     60.00    50.04  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
   624x464       59.95  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
  1680x1050_60.00 (0x2b9) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
maydin@maydin-desktop:~/Desktop$ sudo xrandr --addmode HDMI-0 "1680x1050_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40
maydin@maydin-desktop:~/Desktop$ 

```

---

### Post by Vladlenin5000 on 2015-11-15
Hi and welcome.

What connection are you using? What driver version?

---

### Post by mma-95 on 2015-11-15
> **Vladlenin5000 said:**
> Hi and welcome.

What connection are you using? What driver version?
I am using HDMI cable from graphics card to monitor. I dont know why but when i connect it to motherboard HDMI socket instead graphics card i cant see nothing in the screen.

Driver version is Nvdia binary driver 352.41.

---

