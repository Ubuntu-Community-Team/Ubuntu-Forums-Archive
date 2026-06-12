---
title: "Issues with dual monitors after resume"
date: 2011-11-21
forum: Desktop Environments
---

### Post by jozeph78 on 2011-11-21
Hey all. I'm having issues with my dual monitor setup. Basically, when I come back to my machine after the screen has been disabled (either monitor turned off or full suspend state), only one of my monitors will work. I can usually fix this by switching to a different tty and back to tty7, but sometimes I have to unplug the VGA adapter from my laptop. Worst case scenario, and with increasing frequency, both monitors will stop working and I have to reboot. The computer will not respond to anything. Here's my setup:


[LIST]
[*]HP dv6 laptop (ATI card disabled via Switcheroo, running off of Intel integrated).
[*]Ubuntu 11.10, gnome shell
[*]No Xorg.conf
[/LIST]
```
xrandr output:

xrandr
Screen 0: minimum 320 x 200, current 2970 x 1680, maximum 8192 x 8192
LVDS1 connected 1920x1080+1050+600 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1050x1680+0+0 left (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+   74.9  
   1600x1000      60.0  
   1280x1024      75.0     72.0     60.0  
   1440x900       75.0     59.9  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

---

