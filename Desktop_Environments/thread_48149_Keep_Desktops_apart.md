---
title: "Keep Desktops apart"
date: 2005-07-11
forum: Desktop Environments
---

### Post by Morimando on 2005-07-11
Is there a way to keep Gnome's and KDE's desktop separate?
Because if i populate my desktop with shortcuts to the various partitions in KDE, every time i'm back in Gnome, my desktop looks devastated, because Gnome loads the shortcuts that KDE created, but doesn't understand them and thus there are many "no name" links on my desktop.
Is there a way to have the same shortcuts on KDE and GNOME without this meddle? I basically want the same links on both desktops, but i want them to function, i don't want any "no name" links to appear on my desktop. Oh and if it was possible to have the same icons in both DE (for the said shortcuts), that would be a beauty.

---

### Post by Xian on 2005-07-11
Open the KDE Control Center
Goto System Administration > Paths

Here you should reset a new Desktop path.
Something like: /home/username/kDesktop/

Click Apply.
When it asks you to move the files...confirm yes.

Now you will need to make a new Desktop folder for Gnome.

Open a terminal and enter the mkdir command.
```
$ cd /home/username
$ mkdir Desktop
```

---

### Post by Morimando on 2005-07-12
thanks

---

