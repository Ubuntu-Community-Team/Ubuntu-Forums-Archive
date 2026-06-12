---
title: "disabled KDE, no graphic environment."
date: 2008-11-12
forum: Desktop Environments
---

### Post by fabrile on 2008-11-12
I installed Ubuntu 8.10, after that KDE
and i disabled KDE and everything gone black.
I reboot and I have only system line.
What should I do now to see the graphic environment again
Please, help me.

---

### Post by taurus on 2008-11-12
What would happen if you run startx after you log in with your username and password?

```
startx
```
Or you can start kdm login screen with

```
sudo /etc/init.d/kdm start
```

---

