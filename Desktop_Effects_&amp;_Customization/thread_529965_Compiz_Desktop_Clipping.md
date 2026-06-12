---
title: "Compiz Desktop Clipping"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by spazzedout on 2007-08-19
7.04, ATI 7500 with VGA connected monitor. 

Compiz Fusion (latest). Open Source ATI driver. 


The desktop effects work somewhat fine, albeit choppy at 1024x768. However, if I go to a resolution higher than that - 1280x1200 for example, it cuts most of my desktop off. No wallpaper is displayed, and adding the extra screen size in the Compiz manager has no effect.

What files are involved in the screen resolution/mapping? Any ideas on what would cause Compiz not to render the full desktop? 

thanks

---

### Post by Chymera on 2007-08-22
It is most probably due to your ati card... those guys make fine cards, a lot better than nvidia's, but they seem to have a grunge towards releasing drivers for linux. 
you could try reconfiguring your x, with ye olde:
```
sudo dpkg-reconfigure xserver-xorg
```
and selecting from the available card drivers you find there, but i doubt its going to do much for you.

---

