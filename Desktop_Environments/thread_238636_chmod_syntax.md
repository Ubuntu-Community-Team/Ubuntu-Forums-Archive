---
title: "chmod syntax"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-08-18
**[COLOR="Black"][/COLOR]**

I just converted LimeWire.rpm to .deb via alien

However, my installed program is locked and greyed out.  I'm trying to give myself (root) ownership.  What's wrong with this syntax?  The shell accepts it but the app is still locked. . . 

```
chmod 711 /home/kurt/limewire-free_4.12.4-1_i386.deb

```

---

### Post by aysiu on 2006-08-18
You want ownership? Use *chown*, not *chmod*: ```
sudo chown kurt:kurt /home/kurt/limewire-free_4.12.4-1_i386.deb
```

---

