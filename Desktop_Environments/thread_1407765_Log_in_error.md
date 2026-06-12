---
title: "Log in error"
date: 2010-02-15
forum: Desktop Environments
---

### Post by TroyStachnik on 2010-02-15
when i try to log in to ubuntu, i get an error that says the configuration defaults for GNOME Power management have not been properly installed, please contact system administrator. what is the problem and how might i solve it?

---

### Post by warp99 on 2010-02-17
Run this command:

```
sudo dpkg-reconfigure gnome-power-manager
```

See if this helps.

---

