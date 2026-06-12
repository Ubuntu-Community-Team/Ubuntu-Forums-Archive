---
title: "Cannot enable Desktop Effects presumably after changing &quot;Virtual Resolution&quot;"
date: 2009-07-23
forum: Desktop Environments
---

### Post by Trianos on 2009-07-23
Hi,

I plugged a monitor into my laptop after it had booted into Ubuntu 8.10 and went to change it from the laptop's display to the monitor (since it's bigger and less broken...) and it prompted me that I needed to change the virtual resolution. It asked if it could take care of that for me, so I told it yes... Then all the effects were disabled. Under System > Appearances > Visual Effects tab, "No Effects" was marked and when I try to change it, it tells me "Desktop effects could not be enabled" and that's it. What's strange is that it's asked to change the Virtual Resolution before without this issue. Perhaps something else is amiss, but I'm completely new to this. Thanks in advance for your help.

---

### Post by Trianos on 2009-07-23
Uhm... bump?

---

### Post by realzippy on 2009-07-23
Maybe you should specify your problem by telling us what graphic adapter/driver you use..
Did you (it) enable the extern monitor by xrandr?
what does 

 xrandr -q

say?

---

### Post by Trianos on 2009-07-26
Hello,

I have a Mobile 915GM/GMS/910GML Express Graphics Controller on my notebook - it's integrated, if that helps.

As for xrandr, I did not use it to configure the external monitor. I only used the GUIs in Ubuntu. I will post what xrandr -q produces:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2720 x 900
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

Right now, the monitor is not connected.

---

