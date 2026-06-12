---
title: "Screen resolution problems help!"
date: 2018-02-24
forum: Desktop Environments
---

### Post by g7rfo on 2018-02-24
Hello and I hope someone can help
I have searched everywhere to try and solve this issue I have to no avail!
I installed xubuntu and my screen will only give default connection at 640x480
I have an output from xrandr-q
Failed to get size of gamma for output default
Screen 0: minimum 640x480 current 640x480 maximum 640x480
Default connected 640x480+0+0 0mm x0mm
640x480      73.00*
1024x768_60.00 (0x277) 63.500mhz -hsync +vsync
H: width 1024 start 1072 end 1176 total 1328 skew  0 clock 47.82khz 
V: height 768 start 771 end 775 total 798 clock 59.92hz 

Any ideas what to do to get 1024 ?
I have tried for days? 
Thanks

---

### Post by coinbr on 2018-02-24
Got the same problem here


[LIST]
[*]Just installed Xubuntu 17.10 
[*]Main screen is working just fine in 1080p 
[*]second screen should be used in 1600x900, but I can only set it up to 1024x768 
[*]In second screen I use a passive MiniDP to DVI adapter. It always worked Fedora and Windows
[*]AMD Radeon RX 280x 
[/LIST]


[IMG]https://imgur.com/1mllWyx.png[/IMG]

[IMG]https://imgur.com/UaFlU1y.png[/IMG]




```
xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+  50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  


```

---

### Post by Autodave on 2018-02-24
First of all, coinbr: you need to start your own thread. Mixing threads just causes confusion to everyone.

g7rfo: what video card is in your machine?  Laptop or desktop?

---

