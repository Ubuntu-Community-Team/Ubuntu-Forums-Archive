---
title: "/var/run in Trash"
date: 2006-11-27
forum: Desktop Environments
---

### Post by frspin on 2006-11-27
I have a strage Trash problem
At startup my Wastebasket in full with /var/run files
If I logout and login, now wastebasket is empty

After a reboot, my wastebasket in full with /var/run files.

Problem is recent: about 5 days
I am using Edgy versione with Gnome desktop.

Regards
Franco

---

### Post by endless on 2007-01-04
the file ~/.gnome/gnome-vfs/.trash_entry_cache is the cause. Removing it or moving it to a different file helped...

mv .gnome/gnome-vfs/.trash_entry_cache .gnome/gnome-vfs/.trash_entry_cache_old

good luck!

---

### Post by frspin on 2007-01-04
Good!
It solve the problem
Last line of file must be:
/var/run - 
but was:
/var/run /var/run
I don't know why

Regards
Franco

---

