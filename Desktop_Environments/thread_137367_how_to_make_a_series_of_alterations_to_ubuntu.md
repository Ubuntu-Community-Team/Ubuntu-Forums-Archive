---
title: "how to make a series of alterations to ubuntu"
date: 2006-02-27
forum: Desktop Environments
---

### Post by geuis on 2006-02-27
Hi, I've got ubuntu installed and I have xfce running. I kind of prefer the way it looks compared to gnome and kde, but I'm not particularly partial to anything at this point.

I would like to know how to do a few things that I can't seem to specifically find directions for elsewhere.

The hardware Im using is an older Sony Vaio with 2 hard drives, a cd-rw and a dvd-rom. I would like to have icons for these mount on the desktop when something is inserted. I would also like to have icons for both of my harddrives mount on the desktop too.

Also, in XFCE there is a dock of sorts. I accidentally removed the mozilla firefox icon when I updated to firefox 1.5. How can I add application icons to this dock?

Thanks for the help. Really liking ubuntu so far. I just want to be able to customize it in all the little ways I want.

--Geuis

---

### Post by nalmeth on 2006-02-27
XFCE doesn't seem to have an active desktop like gnome or kde. Gnome uses nautilus to setup the desktop, and if I were a betting man, I'd say KDE uses konqueror.. XFCE is very stripped down and fast, so it has some things not included.

For your mount images, I would recommend using gdesklets, with the appropriate gdesklet you want.
If you don't know, you can install gdesklets with automatix (first result on google), which can also add it to your startup. OR you can use synaptic, or the good ol' terminal:
sudo apt-get install gdesklets

I can't speak either way for its functionality, but try running "nautilus" while in xfce. It will open up the gnome desktop overtop of xfce, while still using xfce stuff (panels theme etc). This may not be a good idea, if it could screw up xfce somehow.. I recommend the gdesklets instead.

To add something to the xfce panel, just right click and "Add New Item"

---

### Post by aysiu on 2006-02-27
Right-click on the "dock" and select "Add to panel."

As for the automounting, press Alt-F2 and type ```
gnome-volume-manager
``` and enter. Then press Alt-F2 again and type ```
nautilus
```. Then make sure in your XFCE Settings that you are saving sessions automatically on logout.

---

