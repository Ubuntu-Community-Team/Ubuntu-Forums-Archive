---
title: "file size discrepancy"
date: 2009-02-20
forum: General Help
---

### Post by uvdevnull on 2009-02-20
I have a few sparse image files, but they're identified as having different size based on which command is used:

```

[devvm1: /home/xen/domains/devmail1.eadev]$ du -ah
1.4G    ./disk.img
40K     ./swap.img

```
```

[devvm1: /home/xen/domains/devmail1.eadev]$ ls -lRh
total 1.4G
-rw-r--r-- 1 root root  40G 2009-02-20 10:32 disk.img
-rw-r--r-- 1 root root 1.0G 2009-02-18 11:14 swap.img

```
Why the discrepancy of 'du' showing actual size and 'ls' showing the maximum possible size of the sparse image file?

---

### Post by uvdevnull on 2009-02-20
Reposted this in the server forum:
[http://ubuntuforums.org/showthread.php?t=1075859](http://ubuntuforums.org/showthread.php?t=1075859)

Can't delete posts here?

---

