---
title: "KDM Doesn't start automatically, but it runs when I type KDM in terminal"
date: 2007-07-24
forum: Desktop Environments
---

### Post by ikkefc3 on 2007-07-24
KDM Doesn't start automatically.
If I set GDM default, GDM starts at startup, but when I set KDM default, it doesn't start, but if I login in the (non graphical) terminal and then type sudo kdm, it runs correctly.
I tried sudo dpkg-reconfigure kdm and set default-xsomething /user/sbin/gdm to /usr/bin/kdm, but i don't get a graphical login at startup.
How can I let KDM start at startup?

---

### Post by luckyd on 2007-07-24
sudo dpkg-reconfigure gdm and set kdm as default...

---

### Post by ikkefc3 on 2007-07-25
> **luckyd said:**
> sudo dpkg-reconfigure gdm and set kdm as default...
Doesn't work. KDM doesn't start at startup.
only when I login and type sudo kdm.

---

