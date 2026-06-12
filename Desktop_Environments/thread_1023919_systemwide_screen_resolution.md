---
title: "systemwide screen resolution"
date: 2008-12-28
forum: Desktop Environments
---

### Post by mommebu on 2008-12-28
Can someone tell me where I can set the screen resolution system wide and consistently in 8.04, i.e. gdm and all users?
I know I can manually edit the xorg.conf, but that involves the risk to loose it again after updates.
The dpkg -reconfigure -phigh thing doesn't do it.

---

### Post by overdrank on 2008-12-28
> **mommebu said:**
> Can someone tell me where I can set the screen resolution system wide and consistently in 8.04, i.e. gdm and all users?
I know I can manually edit the xorg.conf, but that involves the risk to loose it again after updates.
The dpkg -reconfigure -phigh thing doesn't do it.

Hi and you can try the command ```
gksu displayconfig-gtk
```

---

### Post by mommebu on 2008-12-28
Doesn't work neither. Breaks on launching the command.

Thanks anyway...

---

