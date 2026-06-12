---
title: "Trouble installing stuff"
date: 2008-12-03
forum: General Help
---

### Post by munit5000 on 2008-12-03
When I tried installing AWN, it gave me this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.
```

This originally happened to me when I tried installing microsoft fonts I think. Any help would be much appreciated.

Also, I used the mkdir command to (sudo mkdir media/windows) make a folder, but when I try to delete this folder it tells me permission denied. Is there a way to delete this folder?```

```

---

### Post by Elfy on 2008-12-03
You need to add sudo to the error message

```
sudo dpkg --configure -a
```

Likewise you need to use sudo to remove the folder

```
sudo rm -r /path/to/folder
```

assuming that the folder was /media/windows then sudo rm - r /media/windows

---

### Post by munit5000 on 2008-12-03
Both solutions worked perfectly. Thanks!

---

