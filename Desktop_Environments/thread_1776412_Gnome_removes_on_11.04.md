---
title: "Gnome removes on 11.04"
date: 2011-06-06
forum: Desktop Environments
---

### Post by msmith78 on 2011-06-06
Hi, I recently ran apt-get remove lamp-server^ and without noticing gnome was also removed.

How can I fix this.

---

### Post by Cayson on 2011-06-06
```
sudo apt-get install ubuntu-desktop
```This installs the Gnome meta-package.
I am no guru, but it's worth a shot (:

Edit: Also try out this package.
```
sudo apt-get install gnome-session
```

Edit: Run this command to see if GDM is installed at all.
```
sudo dpkg-reconfigure gdm
```

---

