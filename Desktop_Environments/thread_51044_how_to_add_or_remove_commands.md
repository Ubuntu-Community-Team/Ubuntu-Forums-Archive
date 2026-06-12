---
title: "how to add or remove commands?"
date: 2005-07-22
forum: Desktop Environments
---

### Post by bravo_elf on 2005-07-22
For example need to make "sudo gedit /etc/fstab" but when I type it in console, it gives me output like that: "sudo gedit: command not found" so now I need to change the permissions for /etc and fstab to be able to change the it. Its really annoying really... so is there some way to add commands at all?

---

### Post by SGC on 2005-07-22
gedit is not installed in kubuntu, use **kate** or **kwrite** instead:

sudo kate /etc/fstab
or
sudo kwrite /etc/fstab

Or you can install gedit with apt-get, but that is not recommended since it will install many of gnome libraries

---

### Post by wrtrdood on 2005-07-22
... or Nano  ;-)

---

