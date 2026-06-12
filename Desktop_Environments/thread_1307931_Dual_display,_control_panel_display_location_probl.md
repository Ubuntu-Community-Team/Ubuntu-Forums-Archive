---
title: "Dual display, control panel display location problem"
date: 2009-10-31
forum: Desktop Environments
---

### Post by JBAGroup on 2009-10-31
Gnome desktop on Karmic Koala, two monitors.  Desire left monitor (Dell 20" wide screen) to be dominant (control panels resident).  Display positions worked fine in Ubuntu v.8.04.  Now having positioning issues.  

Manipulation of configuration settings using Display Preferences GUI results in left display working fine when right monitor (Dell 19" regular screen) is turned off.  When right turned on (mirror unchecked), control panels displayed in right screen.  Attempted to view/edit /etc/X11/xorg.conf, discovering automatic configuration hiding somewhere (aborted manual edit idea).

Further attempts to resolve issues using Display Preferences GUI showing intermittent variations on available options menu.  1680x1050 resolution available for wide screen (left) monitor when right (legacy size) monitor set to "off".  Wide screen resolution option not present for left monitor when right set to "on".

Two questions:

[LIST=1]
[*]How to correct control panel display location?
[*]How to fix high resolution wide screen option on Dell 20"?
[/LIST]
Otherwise, 9.10 is a considerable improvement!  Thanks for your attention on this one.
nm

---

### Post by reto on 2009-11-19
having the "control panel display location" problem as well. its jhard to work with the gnome-panel on the wrong screen :-(

---

### Post by realzippy on 2009-11-19
You should have a look at xrandr.

Useful would be:

Unplug external monitor,open terminal,type:

**xrandr -q**

post output!

Then plug in 2. monitor,run xrandr -q again,post output!

---

### Post by reto on 2009-11-19
reto@reto-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
reto@reto-laptop:~$ xrandr -q # after plugin in external monitor which for now is black
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
reto@reto-laptop:~$ xrandr -q # after putting the internal monitor on the right of the external one with "Display preferences"
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+1280+224 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)

---

### Post by realzippy on 2009-11-19
So you can change screen position of the monitors,but not
affecting position of gnome panel??

---

### Post by reto on 2009-11-19
right, the panel always stay on my laptop screen except when I turn the laptop screen off completely. before the update they alway where on the left-most screen, which was much more useful to me.

cheers,
reto

---

### Post by realzippy on 2009-11-19
Have a look here:

[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/8152](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/8152)

You could try this script:

#!/bin/bash

if [[ "x$1" == "xon" ]]
 then
 echo "Turning on VGA"
 xrandr --output VGA --left-of LVDS --auto
 echo "Moving panel to second display"
 gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/monitor" --type integer "1"
 gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" --type integer "1"
elif [[ "x$1" == "xoff" ]]
 then
 echo "Turning off VGA"
 xrandr --output VGA --left-of LVDS --off
fi

---

### Post by reto on 2009-11-20
realzippy, thanks a lot, that helped!

---

