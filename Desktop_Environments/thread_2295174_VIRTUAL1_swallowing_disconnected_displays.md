---
title: "VIRTUAL1 swallowing disconnected displays"
date: 2015-09-16
forum: Desktop Environments
---

### Post by adam_clark2 on 2015-09-16
Hi,
  I have two external monitors connected to my laptop via a docking station.
When they are connected xrandr looks like this:
$ xrandrScreen 0: minimum 320 x 200, current 5206 x 1200, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+432 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+   40.0  
...
DP1 connected 1920x1200+1366+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
...
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected 1920x1200+3286+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
...
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

When I un-dock, the VIRTUAL1 seems to gobble up one of my screens:
$ xrandr 
Screen 0: minimum 320 x 200, current 5206 x 1200, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+432 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected 1920x1200+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected 1920x1200+3286+0 (normal left inverted right x axis y axis) 0mm x 0mm
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1920x1200 (0xbf)  154.0MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   74.0KHz
        v: height 1200 start 1203 end 1209 total 1235           clock   60.0Hz





Ofcourse, all my windows are on that screen.  I have had this work before where all my windows collapse onto the one remaining monitor when I undocked, but now it doesn't work

Anyone have any idea how I can stop this behavior?

Adam

---

