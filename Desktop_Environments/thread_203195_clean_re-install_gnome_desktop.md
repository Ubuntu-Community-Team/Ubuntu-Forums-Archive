---
title: "clean re-install gnome desktop?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by davebradford on 2006-06-24
i've been playing around in ubuntu and i think i have messed gnome up a bit, tired failsafe session but i cannot seem to get the desktop back to the way it was after a clean re-install. Any ideas people, i'd be so greatful, any way of clean reinstalling gnome desktop??

thanks.. :)

---

### Post by Mega Man X on 2006-06-24
[QUOTE=davebradford]i've been playing around in ubuntu and i think i have messed gnome up a bit, tired failsafe session but i cannot seem to get the desktop back to the way it was after a clean re-install. Any ideas people, i'd be so greatful, any way of clean reinstalling gnome desktop??

thanks.. :)[/QUOTE]
Did you try to create a new user to see if Gnome works as it was for that user? Because if that fix the problem, perhaps it would be easier to either user a new user or delete all your .gnome and .gconf files at your /home/<user> directory than reinstalling Gnome.

Just an idea ^_^

---

### Post by az on 2006-06-24
This would be an example of how backing up your home drive and reinstalling would not help.

Delete your .gnome and .gnome2 directories (well, move them, don't delete them, in case....) and restart your session.  Stock defaults will be back, I beleive.

---

### Post by az on 2006-06-25
I just tried it. You need to delete the .gconf and .gconfd directories, too.  That's exactly what you want.  You start off fresh.

---

