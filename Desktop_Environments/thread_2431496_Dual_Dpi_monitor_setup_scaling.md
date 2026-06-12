---
title: "Dual Dpi monitor setup scaling"
date: 2019-11-17
forum: Desktop Environments
---

### Post by verline on 2019-11-17
Hi,
I have problem setting up monitors with different resolution, because i can't set scaling factor for each monitor. I have main 4k monitor and second full hd monitor.
While using global scale = 1. i can barely see anything on 4k monitor, because everything is so small. If i set global scale = 1.5 everything on fullhd monitor is zoomed in and too big. I tried to set it up with xrandr, but with no solution. If i set global scale = 1 and scale on xrand for 4k monitor its just zoomed in and blurry. If i tried to zoom out the full hd monitor with global scale as 1.5, full hd 'display' was taking only part of full hd monitor. Has anyone come up with solution to this?
My xrand config:
```
Screen 0: minimum 8 x 8, current 5760 x 2160, maximum 32767 x 32767
DVI-D-0 connected 1920x1080+3840+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95 
   1600x1200     60.00 
   1440x900      74.98    59.89 
   1280x1024     75.02    60.02 
   1280x960      60.00 
   1152x864      75.00 
   1024x768      75.03    70.07    60.00 
   800x600       75.00    72.19    60.32    56.25 
   640x480       75.00    72.81    59.94 
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 621mm x 341mm
   3840x2160     60.00*+  60.00 
   2560x1440     59.95 
   2048x1152     60.00 
   1920x2160     60.00 
   1920x1200     59.88 
   1920x1080     60.00    59.94 
   1680x1050     59.95 
   1600x1200     60.00 
   1600x900      60.00 
   1280x1024     60.02 
   1280x800      59.81 
   1280x720      59.94 
   1024x768      60.00 
   800x600       60.32 
   720x480       59.94 
   640x480       59.94    59.93 
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 disconnected (normal left inverted right x axis y axis)

```
Btw i have nvidia 1060 6gb gpu and Kde Neon (Ubuntu 18.04 based). Cheers.

---

### Post by CatKiller on 2019-11-17
Being able to set display parameters, like scaling or refresh rate, independently for different displays is an area of active development. It may also end up being implemented differently depending on whether you're using X11 or Wayland.

It may not be possible to do what you want with 18.04 without having both displays completely independent, which is a pain to set up and is limited in its usefulness for a single user.

---

