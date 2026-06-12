---
title: "OpenOffice GTK Plugin under other WMs"
date: 2005-03-23
forum: Desktop Environments
---

### Post by apox on 2005-03-23
I have the OpenOffice GTK Plugin installed (openoffice.org-gtk-gnome),
it works perfectly fine when I'm running Gnome or XFCE but doesn't
work when I'm running FVWM.

How do I get it to work under FVWM?

---

### Post by burlap on 2005-03-23
Try running gome-settings-daemon in the background (start it when your fvwm session is started). 

(It's eating up resources, but I used to run it anyway to preserve my gtk themes under windowmaker and fluxbox).

---

### Post by apox on 2005-03-24
Already tried that.. still doesn't activate the OpenOffice GTK Plugin.

---

### Post by pounk on 2005-06-11
I found this in the gentoo forum.. I don't know if this work in ubuntu...


[http://forums.gentoo.org/viewtopic.php?t=26114#463181](http://forums.gentoo.org/viewtopic.php?t=26114#463181)

---

### Post by apox on 2005-06-12
I was able to get a consistent UI across all of my GTK applications as well as OOo by replacing Metacity with FVWM and running GNOME.

The FVWM FAQ has instructions, check it out here: [http://fvwm.org/documentation/faq/#2.8](http://fvwm.org/documentation/faq/#2.8)

---

