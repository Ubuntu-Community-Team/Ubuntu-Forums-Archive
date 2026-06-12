---
title: "Menu icons all the wrong size in xfce - where to change?"
date: 2015-11-15
forum: Desktop Environments
---

### Post by pickarooney on 2015-11-15
All of the standard menu icons for Open, Quit, About, Help, Configure etc in XFCE programs are in 64x64 resolution whereas they should scale down to about 4x4 or 8x8.
This seems to be the case only for my own login. it doesn't happen with root.

Where would this be set?

---

### Post by Dennis N on 2015-11-15
Are you referring to the icons in the drop-down menus within applications, such as mousepad file menu? See image.

---

### Post by pickarooney on 2015-11-15
Yes, exactly!

---

### Post by Dennis N on 2015-11-15
The menu icons are selected based on the method described in the freedesktop.org "icon theme specification": 

[https://developer.gnome.org/icon-theme-spec/](https://developer.gnome.org/icon-theme-spec/)

See the "Icon Lookup" section of this web page for an explanation of the selection routine used. The routine is based on criteria passed to it by the application: name and size. Your icon theme is then searched for a match. If none, backup icon themes are searched. 

There isn't any user input for name or size when this selection routine is used. All we can do is change the icon theme, so I would try that.  

Could you post a screen shot of this problem?

---

### Post by pickarooney on 2015-11-16
I can't manage to - when the menu from mousepad is opened up my PrtScr button no longer works.
I found xfce-theme-manager and tried selecting a different icon set and that has done the trick. The icons aren't as nice but at least they're normal size!

---

### Post by yetimon_64 on 2015-11-16
> I found xfce-theme-manager and tried selecting a different icon set and  *_that has done the trick_*. The icons aren't as nice but at least they're  normal size!         
If you are happy this thread is solved, please mark it as solved using the "Thread Tools" drop down menu on your browser window for this thread; thanks.

Regarding not being able to take a screenshot of a window menu ...
> I can't manage to - when the menu from mousepad is opened up my PrtScr button no longer works.
If I recall correctly the xfce4-screenshooter program has a delay function just like gnome-screenshot (the Unity equivalent for screenshots). Try using the delay function on xfce4-screenshooter to set a timer delay for the screenshot, doing so will give you a few seconds to then open the mousepad menu and wait for the screenshot to work; you can increase the delay if you need more time to open mousepad and its menus etc. 

You are right that just pressing PrntScr won't work while the menu is opened, but using the delay on the actual screenshot program and its timer settings gives you a possible work around for that problem. Cheers, yeti.

---

