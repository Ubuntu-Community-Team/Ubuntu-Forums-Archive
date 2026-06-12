---
title: "Set file permissions for a WHOLE directory (and everything below it?)"
date: 2006-03-03
forum: Desktop Environments
---

### Post by samwh on 2006-03-03
How would I do this? CHMOD only does the Dir itself, not all subdirs, same with changing it in GNOME.

---

### Post by adam.stokes on 2006-03-03
```
chmod -R 777 <dir>
```

-R will recursively get everything beneath top level including subdirs. be careful when recursively setting perms though, you can screw up a box easily.. e.g. chmod -R 777 /

---

### Post by pbaehr on 2006-03-03
Use
```
chmod -R
```
Instead of just chmod to set permissions throughout.

Edit: Too slow, sorry to repeat.

---

### Post by samwh on 2006-03-03
AH! Thanks, should have read the man pages more carefully ;)

---

