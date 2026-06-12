---
title: "Low resolution with Nvidia GT 610 with dual monitor support"
date: 2017-02-19
forum: Desktop Environments
---

### Post by deiks on 2017-02-19
Hello Ubuntu masters,

I'm new at Ubuntu desktop (16.04) so I'm trying to figure out how to solve problem with my low resolution.
I'm using Nvidia GeForce GT 610 (also recognized as GF 119 if anything helps) with dual monitor (both Avalon 225-WT), and native resolution for displays is 1680 x 1050 (I used it on Windows with same configuration).
Displays are connected with, first with VGA cable and second with DVI to VGA adapter, and then VGA cable.

So first when I installed Ubuntu desktop available resolutions was 800x600 and 1024x768. Then when I installed driver I can see 1152x864 and 1366x768.
I tried few ways of installing (which I found by googling) and since I'm new at this I don't know which way is the best to deal with.

So first I tried with Additional Drivers from Control Panel. There were more than one option so I took last version. That didn't made success so I tried going with cvt 1680 1050 60 and adding new mode with xrandr. But problem is when I try to use "addmode" in format ```
xrandr --addmode DVI-I-0 (or VGA-0) "1680x1050_60.00"
``` it says: ```
"Error of failed request: BadMatch (invalid parameter attributes)".
``` I need mention that when I used newmode it created new mode in HDMI section, since my graphic card supports HDMI also.

Last option was that I tried using Ctrl + Alt + F1 and stoping lightdm; sudo init 3; and executing .run file that I downloaded from Nvidia site.

What ever I googled, and what ever I tried, it was useless.

My motherboard also supports display but I'm not using it.

Also, just to mention. My displays are not recognized in display settings. Just seeing "Unknown display".

Best regards, and thank you.

---

### Post by efflandt on 2017-02-20
Unfortunately Linux cannot tell screen resolution when using analog graphics (VGA or VGA from DVI-I) like it usually can when using digital graphics on DVI or HDMI. I have not used xrandr for quite some time, but I did something similar to this when experimenting with VGA from an old laptop connected to a 1080p HDTV, but with different devices and numbers. Although, the laptop had Intel graphics.

Either try the numbers from cvt:```
xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode DVI-I-0 1680x1050
xrandr --output DVI-I-0 --mode 1680x1050

xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-0 1680x1050
xrandr --output VGA-0 --mode 1680x1050
```Or you could try numbers from gtf: 147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync2

I thought I could test that on an old PC (16.04 with GTX 550 Ti) but I cannot find my DVI-I to VGA adapter, so not sure if having digital DVI connected interferes. But I see what you mean. It is able to add the newmode, but not addmode to an output device:```
$ cvt 1680 1050 60
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

$ xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
$ xrandr --addmode DVI-I-2 1680x1050
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected primary 1280x720+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1280x720      59.86*+  60.00  
   1280x1024     60.02  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x2aa) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
```

---

### Post by deiks on 2017-02-22
Didn't helped me using gtf, but thanks on your answer.

---

