---
title: "gdm resolution not correct when I use external monitor"
date: 2009-05-06
forum: Desktop Environments
---

### Post by anando on 2009-05-06
Hi

When I use my laptop all on its own, the gdmlogin  screen shows up at the correct resolution (1440x900) - but when I have an external monitor (preferred 1920x1200) attached to it, the gdm screen on *both* the laptop and the external monitor is very poor (less than 1440x900 - more like [1024x768] and every thing appears very ugly.

Please note that in either case, *after* I login, X seems to settle down to the correct resolution.

How to get gdm login screen at the correct resolution on my external monitor and laptop screen ? Any help will be hugely appreciated.

Regs,
Anando.

Here is my xrandr -q output:
```
$ >> xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 1920 x 2100
LVDS connected (normal left inverted right x axis y axis)
   1440x900       60.0 +
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
DVI-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1 

```

---

### Post by sirdiego on 2009-11-23
Hello,

same problem here. I have a setting with 2 screens (1680x1050 and 1280x1024) is there a solution for that? Its okay, if the 2nd screen (1280x1024) is deactivated with gdm and only starts after logging in.
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 2960 x 1050
DFP1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1400x1050      60.0 +
   1440x900       59.9 +
   1152x648       60.0 +
   640x400        59.9 +   75.1  
   320x200        60.1 +   75.5  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
   640x432        60.0  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
DFP2 connected 1280x1024+1680+10 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+   60.0  
   1152x648       60.0 +
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
   640x432        60.0  
   640x400        75.1     59.9  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
   320x200        75.5     60.1  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
COMPONENT_VIDEO disconnected (normal left inverted right x axis y axis)

```

---

