---
title: "Need root password for the Live CD"
date: 2006-03-31
forum: Desktop Environments
---

### Post by enggabhinandan on 2006-03-31
Hey,
   Do anyone know whats the root password for the Live CD.

---

### Post by aysiu on 2006-03-31
There is none. Use *sudo*, and you won't be prompted for a password on the live CD (you would for a regular Ubuntu install, though).

For example: ```
sudo apt-get update
``` instead of ```
su
apt-get update
exit
```

---

