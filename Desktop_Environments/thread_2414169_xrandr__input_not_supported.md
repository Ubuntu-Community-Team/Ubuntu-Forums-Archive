---
title: "xrandr  input not supported"
date: 2019-03-06
forum: Desktop Environments
---

### Post by jgw on 2019-03-06
I have been trying to set my display to something higher than 1024x768   My monitor is an acer a231h and maximum resolution is 1920x1080 .  So, I entered something like "xrandr --output VGA-0 --mode "1920x1080_60.00"    I had also previously tried to reset my available resolutions and now have:
greg@gregdown2:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  60.00  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

It used to be:
greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1024x768 60.00*
800x600 60.32 56.25
848x480 60.00
640x480 59.94
DVI-0 disconnected (normal left inverted right x axis y axis)
1920x1080 (0x58f) 148.500MHz +HSync +VSync
h: width 1920 start 2008 end 2052 total 2200 skew 0 clock 67.50KHz
v: height 1080 start 1089 end 1095 total 1125 clock 60.00Hz
  
My problem is pretty simple, all I can get, now, is a black screen  telling me "input not supported".  I currently have rebooted the machine and at the recovery menu.  I can goto the root shell prompt and start doing command lines but I have no idea what I should put in the command line as I have already messed it up pretty good.  

Any suggestions would be appreciated - thank you.................

---

### Post by jgw on 2019-03-06
I now have a screen again and xrandr now reports:
greg@gregdown:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      61.00* 
   800x600       61.00  
   640x480       60.00  
  1920x1080-new (0x2c0) 220.640MHz -HSync +VSync
        h: width  1920 start 2056 end 2264 total 2608 skew    0 clock  84.60KHz
        v: height 1080 start 1081 end 1084 total 1128           clock  75.00Hz

When I try again I get:
greg@gregdown:~$ xrandr --newmode 1920x1080-new  220.64  1920 2056 2264 2608  1080 1081 1084 1128  -HSync +Vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

I now, I think, have to start all over but first figure out how to do that.  As far as I can tell I don't have X running either.  getting pretty strange.

Which is obviously screwed up.

---

### Post by #&amp;thj^% on 2019-03-06
> **jgw said:**
>  As far as I can tell I don't have X running either.  getting pretty strange.

Which is obviously screwed up.
To check if X is running:
```
ps -e | grep X
```

---

