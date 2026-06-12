---
title: "Need a shortcut to enable/disable second monitor"
date: 2023-02-04
forum: Desktop Environments
---

### Post by mikber18 on 2023-02-04
Hello, 

I have a dual screen setup, however, my second screen is across the room so its very much a secondary screen. 

I need a way of quickly - toggle on/off - the second screen by pressing a button or an application / gnome-shell extension? that will allow me to quickly toggle the second monitor on/off. 

Does anyone know how this could be done?

---

### Post by #&amp;thj^% on 2023-02-04
First use:
```
 xrandr

```
you will see all screens IE:
```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    120.00*+


```
To turn off my secondary HDMI, I use:
```
 xrandr --output HDMI-0 --off

```
to toggle back on use:
```
xrandr --auto

```
and now:
```
Screen 0: minimum 8 x 8, current 3840 x 2160, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 3840x2160+0+0 (normal left inverted right x axis y axis) 1872mm x 1053mm
   3840x2160     30.00*+  59.94    50.00    29.97    25.00    23.98  
   4096x2160     59.94    50.00    29.97    24.00    23.98  
   2560x1440     59.95  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.98  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DP-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    120.00*+


```
I've never tried with a keyboard shortcut, but an alias in .bashrc should work

---

