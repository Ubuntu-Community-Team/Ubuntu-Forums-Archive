---
title: "Trouble installing theme (I know it sounds stupid)"
date: 2010-01-13
forum: Desktop Environments
---

### Post by Burky on 2010-01-13
I really really really like this them [here ]("http://www.gnome-look.org/content/show.php/Calla?content=52297")

But here's the problem, the archive comes with an Emerald theme, in  which I installed, but that just changes the borders, I want it working in GTK as well. It comes with a folder called GTK, but only has to files in it called "gtkrc" and "menu.png". I don't know how to install that?

Also it says I need the Rezlooks Engine (which I'm unable to find a non-dead linking to a deb of this), and Pixmap Engine (which I cannot find anywhere). 

Anyone care to help me?

---

### Post by ____ on 2010-02-18
I have the same problem with a different theme but I replaced the .gtkrc file in my home folder with the one included with the theme; but that did not do anything. I found out that the pixmap engine is not supported for newer versions of ubuntu, so I changed the ```
Engine "Pixmap"
``` in the .gtkrc to ```
Engine "Pixbuf"
``` which I am assuming is the modern equivalent; but now all of the windows look weird and the theme changer, Appearance application, will not even load.

Sorry that was not that helpful, but maybe, hopefully, it specified the problem.

---

