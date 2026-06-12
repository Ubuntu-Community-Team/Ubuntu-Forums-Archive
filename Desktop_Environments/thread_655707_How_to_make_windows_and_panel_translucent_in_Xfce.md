---
title: "How to make windows and panel translucent in Xfce"
date: 2008-01-01
forum: Desktop Environments
---

### Post by geovino on 2008-01-01
I'm runing Xubuntu 7.10 and I wanted to make the windows and panels translucent. I have the restricted drivers enabled and my video card is nvidia geforce 5200.

How can I enable these tasks?

---

### Post by Telecaster72 on 2008-01-01
I'm in gnome now, but isn't it just xfce menu->system->window manager tweaks. composite tab?
If the composite tab is missing you have to add:

Section "Extensions"
  Option "Composite" "Enable"
EndSection

in the end of xorg.conf

If that does not work check this file:

home/yourusername/.config/xfce4/mcs_settings/wmtweaks.xml
Look for <option name="Xfwm/UseCompositing" type="int" value="1" 
and make sure the the value is set to "1"

Good luck!

Transparent panels does not work so good in xfce though since the icons and text gets transparent as well...

---

### Post by geovino on 2008-01-01
Yes, but it's Settings > Window Manager Tweaks > Compositor tab >  Enable Display Compositing.  

Thanks, it looks good, It's fun using Xubuntu! Quite fast :)

---

### Post by Telecaster72 on 2008-01-02
yes Settings it is, you are right.
Xfce is really nice.

---

