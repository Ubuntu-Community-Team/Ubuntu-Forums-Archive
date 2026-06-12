---
title: "Intel 82Q963/Q965 Dual Monitor setup"
date: 2010-05-28
forum: Desktop Environments
---

### Post by gcave on 2010-05-28
I have an HP Desktop with a Dual Monitor DVI and a analog VGA connection connected to it.  Intermittently one of the monitors will not come back online after a reboot or just in sleep mode (no signal).  I have to go to the panel that has the monitors icon and tinker around with settings until both monitors come back online.  It still spontaneously disappears after going into screen saver without cause or pattern.  

Here are the normal settings:

xrandr -q
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     72.0     70.0     60.0  
   1280x960       60.0  
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

When the box only recognizes a single monitor xrandr -q gives "display not recognized".  This very annoying as it can occur on the primary monitor, which requires me to login via SSH and reboot the box, since I cant get into X.

---

