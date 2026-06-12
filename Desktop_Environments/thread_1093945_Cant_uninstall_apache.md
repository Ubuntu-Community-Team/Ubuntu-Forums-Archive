---
title: "Cant uninstall apache????"
date: 2009-03-12
forum: Desktop Environments
---

### Post by ambdeep on 2009-03-12
I just downloaded apache from the official apache website and installed it using a .tar.gz file......now I cant seem to uninstall it....plz help!!!

---

### Post by klemens on 2009-03-12
depends how you installed it.

.deb file then it's kinda easy
```
sudo apt-get remove apache2
```

if you have compiled from the sources, just go in the directory where you have installed apache and use the next command.
```
make uninstall
```
if i'm not mistaken (i try to avoid this sort of installation)

---

