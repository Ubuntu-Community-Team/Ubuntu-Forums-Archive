---
title: "Hide mounted volume icons"
date: 2005-08-23
forum: Desktop Environments
---

### Post by Domhnull on 2005-08-23
I'd like to hide the desktop icons for mounted volumes but I'm not sure how to do that.  I'd still like them to show on the Places menu, just not the desktop.  Can anyone help out?

Thanks!

---

### Post by lol on 2005-08-23
Gnome comes with a f***ing tool, the "Configuration Editor" (read "regedit" here), that should give you access to some hidden preferences of Nautilus. With this, you can choose if you want the volumes, trash, documents or computer icons visibles on the desktop.

From the command line, just run 'gconf-editor'.

Good luck with the most stupid feature in Gnome!

---

### Post by pmj on 2005-08-23
Applications -> System Tools -> Configuration Editor

Click apps, find nautilus in the list and in there desktop. You need to uncheck the variable volumes_visible.

---

### Post by Domhnull on 2005-08-23
Great!  Thanks, that was very easy.

---

