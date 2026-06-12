---
title: "Two issues with gnome!"
date: 2015-12-07
forum: Desktop Environments
---

### Post by tyklink on 2015-12-07
[LIST=1]
[*]The Gnome display settings are lost on a restart. There is already a solution here ([http://ubuntuforums.org/showthread.php?t=2305134](http://ubuntuforums.org/showthread.php?t=2305134)), but I don't quite understand it and it doesn't apply to my situation. I have two displays on my desktop, but I want the default to be the HDMI port ONLY. Can someone please explain this to me a bit better? Here is my xrandr output if it is needed:```
 Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+  59.94    24.00    23.98  
   1920x1080i    60.00    59.94  
   1280x720      60.00    59.94  
   1024x768      75.08    70.07    60.00  
   1440x480i     59.94  
   800x600       72.19    75.00    60.32  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected (normal left inverted right x axis y axis)
   1360x768      60.02 +
   1024x768      75.08    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   848x480       60.00  
   640x480       75.00    72.81    60.00    59.94  
   720x400       70.08  

```
[*]I am trying to mount a remote FTP server through SSH. I can do everything fine through gvfs, but for some reason it mounts the remote user's HOME directory instead of its entire filesystem. Is there a setting on either machine that will allow me to mount the remote machine's root filesystem by default with gvfs?
[/LIST]

INFO:
My machine is Ubuntu GNOME 15.10 with the latest updates.
The remote machine is elementary OS Freya (GNU/Linux 3.16.0-55-generic i686), probably with it's default shell.

---

