---
title: "gnome-window-decorator, cgwd"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Reb on 2006-08-10
I have cgwd installed, but gnome-window-decorator takes priority. I can kill gnome-window-decorator, and then cgwd themes will apply. How do I do this in a cleaner way. I'm using the xgl.compiz.info packages (Quinn's).
thanks!

---

### Post by murataht on 2006-08-10
1) right click gset-compiz tray icon, select cgwd. (which is under preferences and themes, when you right click on the tray icon).

2) or, add a line in your .bash_profile 

cgwd --replace 

3) or, hack /usr/bin/compiz-start

replace gnome-window-decorator with cgwd ....

good luck

---

