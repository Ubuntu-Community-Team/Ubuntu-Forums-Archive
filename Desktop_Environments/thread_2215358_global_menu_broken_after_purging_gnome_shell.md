---
title: "global menu broken after purging gnome shell"
date: 2014-04-06
forum: Desktop Environments
---

### Post by ELD on 2014-04-06
So, I added gnome-shell using the ppa, didn't like it still and purged it.

Now it seems my nautilus still has the newer menu-bar and global menu seems broken for some apps, like gimp most options are always greyed out.

Any ideas?

---

### Post by sandyd on 2014-04-06
Moved to Desktop Environments

---

### Post by Frogs Hair on 2014-04-07
I have found the Gnome PPA very difficult to remove and even the purge left packages behind . You can try the following command and logout and in . ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

