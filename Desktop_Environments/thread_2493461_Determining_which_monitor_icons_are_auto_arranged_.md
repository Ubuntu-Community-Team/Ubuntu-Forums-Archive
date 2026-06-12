---
title: "Determining which monitor icons are auto arranged onto"
date: 2023-12-16
forum: Desktop Environments
---

### Post by adfh on 2023-12-16
**tl;dr** Ubuntu Mantic with an Nvidia graphics card, with two displays attached, one in Portrait right, keeps snapping my desktop icons when I select for it to arrange them, to the wrong monitor.

I recently migrated my primary home desktop linux install from one computer to another. 

I did a fresh install of the OS overall on the new machine, but migrated my storage drives, including my home directory to the new one.
The previous setup was the latest LTS, and I'm now on Mantic. 
I have deleted my old ~/.config/monitors.xml and then recreated it the way I want (using Display Settings), including copying it to ~gdm/.config/monitors.xml so it would apply to login screen also.

The graphics card I'm now using is an NVIDIA Corporation GK104 [GeForce GTX 760]. 

When booting the machine, the UEFI displays info on what is my primary display, however once in Ubuntu, Ubuntu considers this display "display 2". The display Ubuntu considers my "display 1" is in Portrait (right) orientation.

```

$ xrandr 
Screen 0: minimum 8 x 8, current 3120 x 1920, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1200+0+160 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+  59.88  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected 1200x1920+1920+0 left (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+  59.88  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DP-1 disconnected (normal left inverted right x axis y axis)

```
... am using Nvidia driver metapackage, nvidia-driver-470.

Every time I let Ubuntu "Arrange By -> Keep Arranged", it insists on snapping icons to my portrait display, not my primary landscape display.

I *have* set the primary display (where dock/launcher is).

Any idea how to tell the desktop to put my desktop icons on the display I nominate as primary, and not the secondary one?

Below is what my screen settings look like - they're not lined up because the monitors physically are positioned like that relative to one another, so the mouse cursor roughly travels from display to display on level.
[IMG]https://blogfiles.anthony.hogan.id.au/linkbox/ubuntu-forum-screen-display.png[/IMG]
I did do some searching, and the majority of threads seemed to be from several years ago, with solutions that weren't necessarily appropriate now.

---

