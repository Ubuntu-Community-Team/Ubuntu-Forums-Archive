---
title: "Screen Display Resolution Problem after an update"
date: 2016-10-30
forum: Desktop Environments
---

### Post by Bozoo on 2016-10-30
Hi, 
I upgrade my Ubuntu on 16.10 version a few days ago. 
Tonight i updated my package. Now my resolution is broken. 
My login screen is a little square on the right top and I can't see anything but I can log in my session after write my password. 
When I open my session, the screen resolution is bugged. 
It's like all stuff are zoomed and I can't see my battery/clock & more infos on the left top. 
I have an UX301LA. 
Here some info when I make a xrandr --query & a pictures of desktop : [http://i.imgur.com/pbatZ7y.jpg](http://i.imgur.com/pbatZ7y.jpg). 
When i'm login in recovery mode, my screen resolution is ok. 
I try an old kernel but bug still here. 
Thank's for you help & sorry for my english.
Best, 




```

johan@johan-UX301LAB:~$ xrandr --query
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 8192 x 8192
eDP-1 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   2560x1440     59.95*+
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
  2560x1440_60.00 (0x120) 312.250MHz -HSync +VSync
        h: width  2560 start 2752 end 3024 total 3488 skew    0 clock  89.52KHz
        v: height 1440 start 1443 end 1448 total 1493           clock  59.96Hz

```

---

### Post by Bozoo on 2016-10-30
I add a new screenshot. 
Like you can see width resolution have some bug. 
Best, 
[IMG]http://i.imgur.com/gtQzPQv.jpg[/IMG]

---

### Post by Bozoo on 2016-10-31
Fixed 
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

