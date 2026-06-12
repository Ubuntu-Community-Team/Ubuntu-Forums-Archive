---
title: "Mount USB devices in 'synchronous' mode"
date: 2010-02-04
forum: Desktop Environments
---

### Post by kasatkin on 2010-02-04
Hello!
How can I force Nautilus mounting removable USB devices in "synchronous" mode? Windows XP has settings 'Optimize for quick removal' and 'Optimize for performance' to deal with it.
Modify /etc/fstab not an option.

I use Ubuntu 9.10

Thanks

---

### Post by trueno_ray on 2010-02-04
did you try the option "sync"

---

### Post by kasatkin on 2010-02-04
Yes, modifying /etc/fstab and adding 'sync' option to mount line is working fine, but I need change Gnome default behavior

---

### Post by trueno_ray on 2010-02-08
i'm not sure if it works when you add the config to xinitrc which will be loaded when startup X window

---

### Post by trueno_ray on 2010-02-09
Sorry, u should use gnome-mount

---

