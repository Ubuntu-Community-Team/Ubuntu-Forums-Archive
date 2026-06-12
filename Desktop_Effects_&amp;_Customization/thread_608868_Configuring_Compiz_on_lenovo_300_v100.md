---
title: "Configuring Compiz on lenovo 300 v100"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by goharanwar3 on 2007-11-10
I installed Ubuntu 7.10 on my lenovo 300 v100 (intel 945 GM chipse).
when i go in the Appearance->advanced compiz settings ,i cant mark/tick any option.although i can see all the effects options but not able to select any of them.
please help me with this. i tried different methods that i read from different threads but none worked.
thanks

---

### Post by goharanwar3 on 2007-11-10
well..can someone tell me that how can i restore the default settings in Gutsy.I will again try to configure it from the beginning
thanks

---

### Post by su3180 on 2007-11-13
hello... have a lenovo too... try this: System -> Preference -> Appearance; select "Visual effects" and click a radio button according to your wishes.

It might be that you have a backlisted video driver and they do not work "out of the box"; here is what you can do:

1) navigate to your home directory; open ".config" folder;
2) create "compiz" folder (skip this step if you have it)
3) create file named "compiz-manager", open it and write "SKIP_CHECKS=yes" (without quotes)
4) restart graphics (CTRL+ALT+BACKSPACE)
5) try your video playback with some movie you have around and move playback window - in my case, system did not redraw correctly the desktop ("screenshots" are visible in previous window position)
6) if you have this problem too, try the following: open "gconf-editor" (use synaptic to install if not available)
7) navigate to this key: /apps/compiz/plugins/move/allscreens/options/lazy_positioning
8) unckeck it

during playback, your window menus might flicker, but I think it's a small price to pay for compiz...  ;)

---

