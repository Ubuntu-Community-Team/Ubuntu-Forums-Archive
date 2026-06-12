---
title: "Dell U2412M Monitor: randr does not list any output ports"
date: 2012-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lmorda on 2012-02-18
My **Dell U2412M** Monitor **works with Ubuntu 11.10**, but **does not work with Ubuntu 10.04**.  I am unable to list any output ports with the randr command, and so I don't see how I can change my resolution.  

**Ubuntu 11.10:**

```

louis@loubu:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
DVI-1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  

```**Ubuntu 10.04:**

```

louis@loubu:~$ xrandr
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0* 
   1280x1024       0.0  
   1280x960        0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
louis@loubu:~$
louis@loubu:~$ cvt 1920 1200
   # 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
   Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
louis@loubu:~$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
louis@loubu:~$ xrandr --addmode DVI-1 1920x1200_60.00
   xrandr: cannot find output "DVI-1"

```

How can I setup my monitor to work in Ubuntu 10.04?  Are there drivers I can download somewhere?  I can't seem to find them anywere.  Can I use the randr command to force my resolution?  I don't understand how I can without any output ports being listed.  I'll always get a "xrandr: cannot find output" error.

Thanks.

-Louis Morda
 SAIC Computer Scientist

---

