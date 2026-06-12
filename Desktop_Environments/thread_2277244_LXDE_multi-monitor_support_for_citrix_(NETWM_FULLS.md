---
title: "LXDE multi-monitor support for citrix (NETWM_FULLSCREEN_MONITORS)"
date: 2015-05-07
forum: Desktop Environments
---

### Post by Chid_Kool on 2015-05-07
Am using LXDE with Citrix Receiver 13.1.2 on Lubuntu 14.  With 2 monitors, my ICA session does not span across both screens.

'wfica -span h' gives an error Window Manager does not support multi-monitor.

[COLOR=#666666][FONT=proxima-nova]xprop -root [/FONT][/COLOR][COLOR=#666666][FONT=proxima-nova]_NET_WM_FULLSCREEN_MONITORS [/FONT][/COLOR]which Citrix depends on to do the span returns 'not found'.  

Is there a way I can make this work ie) enable the _NET_WM_FULLSCREEN_MONITORS using some xorg.conf setting in LXDE?  
Or should I change my Window Manager itself?

---

### Post by Chid_Kool on 2015-05-07
I ran this command on a gnome desktop and see this prop set.
[COLOR=#666666][FONT=proxima-nova]xprop -root | grep _NET_[/FONT][/COLOR][COLOR=#666666][FONT=proxima-nova]WM_FULLSCREEN_MONITORS

[/FONT][/COLOR]What is the way to enable/disable these xprops?  I really want a light X window manager, and would prefer LXDE over anything else.

---

