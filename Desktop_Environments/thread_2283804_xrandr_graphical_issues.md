---
title: "xrandr graphical issues"
date: 2015-06-24
forum: Desktop Environments
---

### Post by epestsov on 2015-06-24
I have a problem with xrandr.
I have one Nvidia 460 card :
```
 :~$lspci|grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
```
I have 2 monitors (1080*1920) connected to it, all I want to have is to have [COLOR=#ff0000]Clone[/COLOR] mode.
By default my PC boots up with cloned monitors but with panning enabled, so if I move my mouse to the right I can see a black screen.
xrandr outputs following:

```
 :~$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 640mm x 360mm panning 3840x1080+0+0
   1920x1080      60.0*+   59.9     50.0     30.0     25.0     24.0     24.0     60.0     50.0  
   1360x768       59.8  
   1280x1024      60.0  
   1280x720       59.9     50.0  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        59.9     59.9  
DVI-I-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 475mm x 267mm panning 3840x1080+0+0
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9
```

To disable the panning mode I can use the command 
xrandr --output HDMI-0 --panning 0x0+0+0 && xrandr --output DVI-I-2 --panning 0x0+0+0
However changing modes with xrandr leads to graphical issues with more than 50% chance (can make a video of that if somebody wants)
But if it the command was successful the setup stays until next reboot.
All above is true for GUI changing (with KDE settings-display)

I tried to put xrandr command in autorun (KDE settings-startup) or /etc/kde4/kdm/Xsetup but it didn't work - the system starts with panning.

Can someone help me with that?

---

