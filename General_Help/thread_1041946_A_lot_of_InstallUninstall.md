---
title: "A lot of Install/Uninstall"
date: 2009-01-17
forum: General Help
---

### Post by subzero.amir on 2009-01-17
If I do a lot of install/uninstall of softwares, will it slows my system? (like windows)

Thanks...

---

### Post by Tim Sharitt on 2009-01-17
If you install a lot of applications which run in the background, it will slow any system. Otherwise, it shouldn't cause ant problems. The packages downloaded by apt will start taking up room after a while, but cleaning them out is fairly straight forward.
```
sudo apt-get clean
```

After you uninstall an application, you may have dependencies installed Which are no longer needed. They can be easily removed as well.

```
sudo apt-get autoremove
```

---

### Post by 3rdalbum on 2009-01-17
No, unless the adding and removing causes disk fragmentation. When Windows becomes slow, it's not due to disk fragmentation.

---

### Post by Tim Sharitt on 2009-01-17
> **3rdalbum said:**
> No, unless the adding and removing causes disk fragmentation. When Windows becomes slow, it's not due to disk fragmentation.

From what I understand, ext3 doesn't have the problems with fragmentation that Windows filesystems are prone to.

---

