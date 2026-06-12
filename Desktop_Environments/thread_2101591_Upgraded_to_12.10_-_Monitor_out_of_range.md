---
title: "Upgraded to 12.10 - Monitor out of range"
date: 2013-01-05
forum: Desktop Environments
---

### Post by adrianlm2 on 2013-01-05
Hello,

After a lot of googling, this is my last resort. I recently upgraded from 12.04 to 12.10 (64bit) and now my secondary monitor cannot be set to its native resolution (1920x1080) or to my preferred resolution (1680x1050). However, I can set the monitor to any resolution below 1680x1050.

I have a radeon hd6950. I tried using xrandr to force the appropriate mode to no avail. 

I've also tried messing with boot-repair and grub. Some online sources mentioned uncommenting a specific line so that grub runs at safe resolution. This however did not work for me. To be fair, I didn't expect this to work since it was meant to fix "out of range" errors when booting...

If I should provide any other information, please let me know. Thank you.

EDIT: After looking at other forum posts, I realized I forgot to specify some information.

I'm currently using the open source drivers.

The output to xrandr -q is shown below. DVI-0 is the problematic monitor.

> 
adrianlm@adrian-ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1680x945+1680+105 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080      60.0 +   50.0     24.0     25.0     30.0  
   1680x1050      59.9  
   1680x945       60.0* 
   1400x1050      74.9     59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       50.0     60.0  
   1440x576       25.0  
   1024x768       75.1     70.1     60.0  
   1440x480       30.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
DVI-1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1680x945       60.0  
   1400x1050      74.9     59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  



---

### Post by YannBuntu on 2013-01-05
Please run Boot-Repair --> Advanced options --> "GRUB options" tab --> tick "Uncomment GFXMODE" --> Apply
Indicate the new URL that will appear?
Reboot and indicate what you observe?

---

### Post by adrianlm2 on 2013-01-06
Hello and thank you for the reply.

Unfortunately, I had already tried that method to no avail. I can boot into Ubuntu just fine, but the valid resolutions for my **secondary** monitor are still limited to those below 1680x1050.

EDIT:
Sorry I forgot to provide the URL. I will do this as soon as possible.

---

