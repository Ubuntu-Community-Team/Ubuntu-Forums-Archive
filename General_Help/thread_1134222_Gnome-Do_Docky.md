---
title: "Gnome-Do Docky"
date: 2009-04-23
forum: General Help
---

### Post by paradigm2 on 2009-04-23
Sort of a continuation of the closed thread from the old Jaunty forum

[http://ubuntuforums.org/showthread.php?t=1037447&highlight=gnome](http://ubuntuforums.org/showthread.php?t=1037447&highlight=gnome)

I have GNOME Do v0.8.1.3 installed from the Gnome-Do repository.  I like it a lot.  However, how may I move it either to the top or tell it not to stay in the bottom centre but more off to the bottom right (just left of the workspace switcher and trash bin).

---

### Post by pbpersson on 2009-04-24
I doubt very much that you will ever get it to display off-center, that is just my suspicion.

However, I did move it to the top of the screen.

It was.....well, I thought it would be a simple selection in the preferences of Do but it was not - at least not that I could find.

I had to use the gconf-editor to modify the value of the following key:

/apps/gnome-do/preferences/Docky/Utilities/DockPreferences/Orientation

---

