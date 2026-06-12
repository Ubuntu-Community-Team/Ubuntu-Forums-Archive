---
title: "Set resolution for VNC on headless system"
date: 2011-08-18
forum: Desktop Environments
---

### Post by benjio123 on 2011-08-18
Hey all, I've been googling for hours and can't figure this out!
I'm running a headless server, and I do all of the administration via VNC (x11vnc server, native OSX client). I want to set the resolution sent by the vnc display to match my macbook's native 1440x900. I have set an argument -geometry 1440x900 on the VNC server, and it sends a stretched 1024.768 display :/
When I go to System>Preferences>Monitors the max it lets me set is 1024x768.

Here is what I've tried:
```

bensanders@Server:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

bensanders@Server:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       58.1 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

bensanders@Server:~$ gtf 1440 900 60

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

bensanders@Server:~$ xrandr --newmode "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

bensanders@Server:~$ xrandr --addmode LVDS1 1440x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

Any Ideas? help is much appreciated! Any way to set other than through xrandr?? Most posts say to edit your xorg.conf, but I don't have one!

---

