---
title: "Strange problem with Eterm transparency"
date: 2005-04-04
forum: Desktop Environments
---

### Post by digby on 2005-04-04
So I'm using eterm in KDE.  But when I set it to its pseudotransparent background either by using the option --trans with the command or the menu funtion once it is loaded, it shows the wallpaper from Gnome instead of my KDE background... 

Anyone know what would cause this or how to fix it?

---

### Post by Juergen on 2005-04-05
AFAIK Eterm's transparency is just 'simulated' by copying the background of the root-window.
So it seems KDE is managing it's own, 2nd, background image.

You could experiment with 'xsetroot -bitmap' - if this changes something, search for all places where a background can be set. 
No KDE here, so you have to search yourself ;-)

---

