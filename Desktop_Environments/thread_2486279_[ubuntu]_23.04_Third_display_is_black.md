---
title: "[ubuntu] 23.04 Third display is black"
date: 2023-04-25
forum: Desktop Environments
---

### Post by karolbednarz on 2023-04-25
I have an issue after updating to Ubuntu 23.04
If I try to use 3 displays - build in Laptop display + 2 External - one connected via HDMI second via USB-C, the USB-C display is detected but its all black.
Tried to change Frequency and resolution but it didnt solve the problem. I check the similar issues on the forum from previous version of ubuntu but none of them resolve the problem.
Wire and display are working fine as when I connect only one external display with USB-C it works just fine, same if its only one external display connected via HDMI.


```
 $ xrandr -q
Screen 0: minimum 320 x 200, current 5760 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+3840+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.00*+  60.00  
   1680x1050     60.00  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     60.00  
   1400x900      60.00  
   1280x960      60.00  
   1440x810      60.00  
   1368x768      60.00  
   1280x800      60.00  
   1280x720      60.00  
   1024x768      60.00  
   960x720       60.00  
   928x696       60.00  
   896x672       60.00  
   1024x576      60.00  
   960x600       60.00  
   960x540       60.00  
   800x600       60.00  
   840x525       60.00  
   864x486       60.00  
   700x525       60.00  
   800x450       60.00  
   640x512       60.00  
   700x450       60.00  
   640x480       60.00  
   720x405       60.00  
   684x384       60.00  
   640x360       60.00  
   512x384       60.00  
   512x288       60.00  
   480x270       60.00  
   400x300       60.00  
   432x243       60.00  
   320x240       60.00  
   360x202       60.00  
   320x180       59.99  
DP-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00 +  74.99*   50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00    60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00 +  74.99*   50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08
```


[update]
when doing 
```
 xrandr --output DP-1 --brightness 0.9
```
sometimes it brings the screen to work. Happens that it disappear again after a minute or so. It looks like if you send some message to the display (like changing brightness) it can awake.
As well if you open some apps that are loading on that screen (in my case WebStorm) it switch of the display, and sometimes goes back but sometimes stays black.

---

### Post by karolbednarz on 2023-04-25
another strange thing that noticed, when start the laptop with all three displays connected, it happended that all 3 displays were working up to the login screen, when i put the password and got to the destkop one display (USB-C) turn black.

---

