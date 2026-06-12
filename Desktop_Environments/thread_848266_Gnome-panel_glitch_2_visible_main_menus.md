---
title: "Gnome-panel glitch: 2 visible main menus"
date: 2008-07-03
forum: Desktop Environments
---

### Post by dsavi on 2008-07-03
I am new to Ubuntu forums, but I have to say that I like the look of it. Most posts seem intelligent and with good intentions. These forums have helped me before, in fact, about 3 times just yesterday. But now even after an extensive search I haven't been able to find an answer to this question so I decided to ask myself.
My gnome-menu is broken, and I don't know how to fix it. I have not one but 2 or 3 main menus (Depends how you look at it- when I restart it there's another one under my name) all of which work, and I don't want as I will be attempting an install of macmenu soon. There's also an applet which it won't let me close, let alone right click on or use. Here's a picture:
[IMG]http://img363.imageshack.us/img363/7415/malfunctionmenuae6.png[/IMG]
My most educated guess I can come up with is that to fix it I would have to reset the configuration file, but I don't know how to do that.:confused:
If you need any more information, just ask. Thanks in advance for any help I get.
Oh yes, and while I'm at it, I can't find Emerald theme manager anywhere on 8.0.4, anyone know how to start it?
~dsavi

---

### Post by Sam Lars on 2008-07-11
You can always try reinstalling the panel.
```
sudo apt-get remove gnome-panel; sudo apt-get install gnome-panel
```
Or you could delete that panel and start over with a new one.

Emerald Theme Manager isn't in System > Preferences?

---

### Post by FerN(SA) on 2008-07-14
Just right click on the second menu and click remove from panel

---

