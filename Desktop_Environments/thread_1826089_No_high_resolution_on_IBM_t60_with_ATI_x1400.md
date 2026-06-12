---
title: "No high resolution on IBM t60 with ATI x1400"
date: 2011-08-16
forum: Desktop Environments
---

### Post by tdi on 2011-08-16
HI, 

I salvaged good old T60 machine, with ATI X1400 and hi resolution screen (1600x1200). My problem is that Ubuntu does not detect higher resolutions than 1024x768. I can that radeon driver is sed (xserver-xorg-video-radeon). When I install fglrx drivers, the systems seems not to see 3d acceleration at all, legacy gnome starts and still can't change the resolution. 

Additionally xrandr shows, look at maximum ... it is something wrong. 
tdi@congruence:~$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum **8192 x 8192**
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 285mm x 214mm
   1024x768       60.0*+
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

Has anybody encountered such a problem before? Probably ATI X1400 issue, not thinkpad.

---

