---
title: "USB Flash Drive?"
date: 2006-05-05
forum: Desktop Environments
---

### Post by JBL on 2006-05-05
Why won't my USB flash drive auto-mount in Xubuntu? It Auto-mounted in GNOME,why won't it now?

---

### Post by JBL on 2006-05-05
*Fixed

---

### Post by ranf on 2006-05-05
How did you fix it?
Others might be interested in this as well.

---

### Post by JBL on 2006-05-06
I did a search on google for xfce4-mount-plugin. i installed it, then i typed in terminal 'sudo apt-get install gnome-volume-manager.'  Now every time i plugin in my USB Flash drive i open a terminal and put 'sudo gnome-volume-manager.' it automatically mounts it for you. After all that just click open the mount plugin.

---

### Post by aysiu on 2006-05-06
You don't need to do ```
sudo gnome-volume-manager
```

Go to the XFCE Settings and make sure you select to save your session on logout. Then, press Alt-F2 and type ```
gnome-volume-manager
``` That's it. No *sudo* needed.

---

