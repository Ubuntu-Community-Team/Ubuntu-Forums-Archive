---
title: "Window Selection and Window dominance"
date: 2009-02-05
forum: Desktop Environments
---

### Post by culainn on 2009-02-05
Folks,

New to the forums and Ubuntu for that matter. Had a good browse of the posts for assistance but could find none that might help. Anyway, I am using Gnome Version: 2.24.1 on 8.10. love it BTW. Anyway, my issue is this - when I have a window or series of windows open on the Desktop, and I  select an app from The Applications Menu, the window for the selected app will open behind the currently opened window (this doesn't sound to clear on reading....). In order to access this recently opened app I have to select it from panel or minimise the dominant window(s) This also applies to opening hyperlinks in a document or an email, etc. In short how do I alter the dominance of the windows?
I hope this is clear

Thanks

C

---

### Post by gettinoriginal on 2009-02-05
Assuming that you are running compiz, try this in terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
It resets compiz to all default settings
Also assuming that you have "window list" applet on your panel(shows minimized windows), right click, preferences, "show windows from current work space"  :p

---

