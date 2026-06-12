---
title: "Looking for KDE app - let's you reboot to specific OS"
date: 2009-08-10
forum: Desktop Environments
---

### Post by spaceboy909 on 2009-08-10
I think I remember seeing this in another distro with KDE one time.  It was a great feature.  When you selected to reboot, it would allow you to select to reboot into Windows, thereby temporarily bypassing the GRUB menu and its' default settings.  

I would like to be able to use this in Gnome.  I'm currently running Ibex.

Ftr, I'm NOT looking for 'startup manager'.  I already have this, and that is for long term changes.

---

### Post by spaceboy909 on 2009-08-10
Maybe it might be more feasible to just add a manual menu item with the appropriate commands.  If someone can tell me how to do that, that would be fine.

---

### Post by froghopper on 2009-08-10
You might be thinking of [Nextboot]("http://www.kde-apps.org/content/show.php/Grub+Nextboot+German+Version?content=41474&PHPSESSID=e5af") although it seems rather dated. The script is complex for parsing the grub menu.lst but the command that does what you want is **savedefault**

```
echo "savedefault --default=2 --once" | grub --batch
```

should start the 3rd item in the grub menu on reboot (--default=2 with items numbered 0, 1, 2 etc)

---

