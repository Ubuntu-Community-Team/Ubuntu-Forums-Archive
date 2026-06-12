---
title: "No listing for LG W2242TQ Monitor"
date: 2008-08-20
forum: Desktop Environments
---

### Post by fballem on 2008-08-20
On my system, the generic monitor is selected. When I access Screens and Graphics to identify the specific monitor, there is no listing for the LG W2242TQ monitor.

Is there another monitor setting that will work, or do I need to do something else. The monitor resolution is correct at 1680x1050, but the frequency should be 60Hz, not the 50Hz that is currently showing.

Thanks,

---

### Post by kagashe on 2008-08-22
> **fballem said:**
> On my system, the generic monitor is selected. When I access Screens and Graphics to identify the specific monitor, there is no listing for the LG W2242TQ monitor.

Is there another monitor setting that will work, or do I need to do something else. The monitor resolution is correct at 1680x1050, but the frequency should be 60Hz, not the 50Hz that is currently showing.

Thanks,
Try using xrandr command.
$ xrandr -q
This will display the monitor and current resolution e.g. what I get is as follows:
> ~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 270mm x 200mm
   1280x768       60.0  
   1152x768       54.8  
   1024x768       60.0* 
   800x600        75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     60.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
LVDS connected (normal left inverted right x axis y axis)
   1024x768       60.0 
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

The * shows the current mode.

In your case * mark will be there for the following entry:
> 1680x1050	50.0*
If it displays 60.0 also against this resolution you can change it with the following command:
> $ xrandr --output VGA-0 --rate 60.0

But I think 60.0 may not be available for 1680x1050 in your case.

kagashe

---

### Post by fballem on 2008-08-22
Thanks for the reply. Tried the commands, and as you had suspected, 60.0 was not available.

Interesting, since I have an NVidia GeForce 8600GT with 512 meg ram, so it's not the graphics card.

Ah well

Thanks!

---

