---
title: "How to completely uninstall then reinstall gnome"
date: 2010-03-14
forum: Desktop Environments
---

### Post by JPA2 on 2010-03-14
Is there a way to completely uninstall gnome and then reinstall it via the terminal?
My gnome is jazzed and cannot get to synaptic package manager.:-(

---

### Post by Method X on 2010-03-14
Hi.
Just logout, then ALT+F1 or [2,3...6].
Login there.
Type:
```
sudo aptitude purge gnome-desktop-data
```

purge command will completely uninstall package and it configuration files.

This will delete all packages.
reboot and install it:

```
sudo aptitude install gnome-desktop-data
```

---

