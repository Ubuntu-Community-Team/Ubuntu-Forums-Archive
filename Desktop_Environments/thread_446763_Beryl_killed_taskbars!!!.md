---
title: "Beryl killed taskbars!!!"
date: 2007-05-17
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-05-17
Been having a play with my edgy machine, installed beryl-manager  & beryl, had a play, looks quite nice, tried to go back to standard gnome gui, no taskbars!, no max,min & close buttons!
how can I fix it?
i uninstalled all the beryl stuff but no good!
Help!!

---

### Post by mister_p_1998 on 2007-05-17
Ok I  found if I create a new user, their taskbars are ok, how do I copy their taskbar/gnome setting to mine?

---

### Post by mister_p_1998 on 2007-05-18
I Fixed it myself!

delete the following Dirs...

 .gconf 
 gconf .
 .gnome 
 .gnome2 
 .metacity 
 .nautilus 
 .gtk-bookmarks 
 .local 
 .bash_profile 
 .bashrc 

That resets Gnome prefs and restore taskbar max,min & close.
you just have to set your personal prefs like screensaver, background etc.
Steve

---

