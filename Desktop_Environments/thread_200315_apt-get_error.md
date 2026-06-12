---
title: "apt-get error"
date: 2006-06-20
forum: Desktop Environments
---

### Post by unisol on 2006-06-20
when i try to use apt-get update i get this messagept-get: error while loading shared libraries: ndexSaIS2_EESsSsSsb: cannot open shared object file: No such file or directory is there a fix for this

---

### Post by RAOF on 2006-06-20
That sounds **really** bad.  Is everything on your system broken, or just apt-get?  If it's just apt-get, then you might be able to try:
```
sudo aptitude reinstall apt
```.  If that doesn't work, then you've got some fairly serious problems :(

---

