---
title: "Revert all changes from gnome"
date: 2011-11-26
forum: Desktop Environments
---

### Post by samg34 on 2011-11-26
Lets get this out-- I screwed up gnome
I don't know what I did, but it looks more like Gnome 2.x.
Is there a way to revert all of the changes to gnome?
I tried reinstalling, but it didn't really help much.

---

### Post by samg34 on 2011-11-26
To clarify, I only reinstalled gnome3 not the entire OS.
Would that maybe reset my customizations?

---

### Post by samg34 on 2011-11-27
I tried
```
rm -r .cache .config .dbus .dmrc .gconf .gnome2 .mission-control
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```
and but it still didn't change anything

---

