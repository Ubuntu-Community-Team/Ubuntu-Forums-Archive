---
title: "modprobe"
date: 2005-03-02
forum: Desktop Environments
---

### Post by nevlenc on 2005-03-02
How to add automatic sound card module starting. i have to all time add sound card module with modprobe. Where write it?

---

### Post by p!=f on 2005-03-02
/etc/modules
and after you edit it run
```

sudo update-modules

```
reboot to confirm it works :)

---

