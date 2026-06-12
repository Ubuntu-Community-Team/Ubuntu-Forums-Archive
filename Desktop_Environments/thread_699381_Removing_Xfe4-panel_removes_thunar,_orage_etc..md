---
title: "Removing Xfe4-panel removes thunar, orage etc.?"
date: 2008-02-17
forum: Desktop Environments
---

### Post by chochem on 2008-02-17
I recently went from Ubuntu to Xubuntu, which prompted me to read up on the subtleties of what's what in an X windows system ("desktop environment", window manager, etc.) I then went on to disable xfce4-panel and install the gnome-panel package, setting up a single bottom window gnome panel. 

Seeing as I thought that I'd learnt that the xfce4-panel was just a part of the big xfce4 goodie bag, by no means central or essential, I figured that uninstalling it should be perfectly doable. However Synaptic tells me that uninstalling it will also affect the xfdesktop, thunar and orage (apart from the panel plugins which is understandable), all of which are perfectly useable when I'm not running the xfce4 panel. 

What gives? I figured that maybe the xubuntu-desktop metapackage provided some sort of glue but uninstalling it didn't make any difference.

---

### Post by kaiju on 2008-02-18
both thunar and orage get removed with xfce4-panel because it is a dependency for them both. that means you technically cannot have thunar or orage installed on your system without also keeping xfce4-panel. but having it isntalled doesn't of course mean that you also have to use it :)

(for a look at the dependencies of any package, you can use synaptic or 'apt-cache show package-name' from the terminal.)

---

### Post by chochem on 2008-02-21
Ok thansk for that, kaiju. I know about dependencies, it just didn't make much sense to me that these things should be interconnected in any way but simple bundling. But then what do I know about programming :)

---

### Post by kaiju on 2008-02-22
i know close to nothing about programming, but i think it is possible to mess around with the packages and change their dependencies, if you're really so mad at xfce4-panel.
then again, the few kilobytes saved are probably not worth the hassle (and possible complications) :p

---

