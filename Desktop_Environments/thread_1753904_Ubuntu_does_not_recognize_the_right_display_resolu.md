---
title: "Ubuntu does not recognize the right display resolution"
date: 2011-05-09
forum: Desktop Environments
---

### Post by 5hpir3 on 2011-05-09
Hi,
I have set up ubuntu 11.04 on my desktop pc. But in the settings panel, the right screen resolution is not display. I only can select 800x600, 1024x768 and 1280x1024... xrandr tells me 
```
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
```and```
 xrandr --output VGA1 --mode 1920x1080
``` works really well but is not persistent and the desktop manager does not seem to accept the settings right, so in the top bar some icons are doubled and the left sidebar does not go down to the ground...
any hints?

---

