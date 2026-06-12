---
title: "Radeon Mobility 9200 (AGP) and xrandr [Hardy]"
date: 2009-02-17
forum: Desktop Environments
---

### Post by whizdom on 2009-02-17
Hi all,

I recently got a Radeon Mobility 9200 (AGP) for my desktop.  The desktop has an onboard Intel graphics card. The desktop's plugged into two monitors.  During bootup, the desktops get a mirrored output, however, as soon as the GDM login screen shows up, only one of the monitors gets the output.  I'm using Ubuntu 8.04 (Hardy).

I have removed the xorg.conf file so there's no xorg.conf involved.  Here's xrandr output:
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1280 x 1200
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0     59.9  
   1152x864       75.0*    74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

What steps could I take to get Ubuntu to detect the second monitor?  I've gone through the forum, but still no concrete solution.

Please let me know if you require clarification.  Thanks in advance for your help!

---

### Post by whizdom on 2009-02-18
Found the solution:

Its similar to what [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) say, except we use:

xrandr --output DVI-0 --set load_detection 1

This should help force detect the screen.  You can also set a monitor with appropriate modlines in the xorg.conf file to help xrandr detect the right modes.

I tried adding the following lines to force Ubuntu to detect the DVI input at boot time, however that didn't help.  I still need to run the above command line to get things going.

Option "Ignore"		"false"
Option "Enable"		"true"
Option "PreferredMode"	"1152x864@75"

We could run that command line at boot time in our boot up scripts, however, let me know if someone knows a clean Xorg way of forcing DVI-0 to be load detected.  

Thanks.
-Vivek.

---

