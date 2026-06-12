---
title: "modify gnome-panel separator?"
date: 2009-09-12
forum: Desktop Environments
---

### Post by pelle.k on 2009-09-12
How would one go about to change the look of the default gnome-panel separator items/applets? The default separators go from the absolute top of the panel, to the absolute bottom, where i would like to add a bit of padding (a few pixels) to the top/bottom of the separators.
Even better, if i could do the actual graphics myself from a bitmap (png/jpg or what have you).
Is there a way to do this using themeing (gtkrc), or does anyone know any other way to achieve this?

---

### Post by Lucre on 2009-11-14
It's not a great solution, but what I've done is to make a custom launcher, and assign the image I want to use for my separator to it.  If you use "gnome-panel" for the command, then nothing meaningful happens if you accidentally click your "separator".  What I found to be the most convenient way to do it was to create the launcher on the desktop, then drag it to the places I wanted it on the panel.

---

### Post by pelle.k on 2009-11-14
Thanks for the suggestion. I've been doing something like that actually. I guess one has to actually modify the source code for that particular applet (or maybe the gnome-panel source) for that to happen. Bummer!

---

