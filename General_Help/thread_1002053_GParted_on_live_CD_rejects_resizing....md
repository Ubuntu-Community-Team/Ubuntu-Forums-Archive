---
title: "GParted on live CD rejects resizing..."
date: 2008-12-04
forum: General Help
---

### Post by mjta on 2008-12-04
I've been trying to resize /dev/sda1.  I get an error that asks me to run e2fsck -f /dev/sda1 .  (It asks politely, as well.)
So I went into the terminal, and typed:
```
sudo e2fsck -f /dev/sda1 && sudo resize2fs /dev/sda1 (and then the size)
``` 
e2fsck works fine.  resize2fs still asks me to run e2fsck first.  I just did!

I'm terribly confused, and I ended up needing to resort to a closed-source tool. (gasp!)
Perhaps someone has a solution?

---

### Post by mikewhatever on 2008-12-04
In many cases, /dev/sda1 is an ntfs partition with Windows on it. If that's the case, you should try running disk check utility in Windows, after that, Gparted should be able to resize it.

---

### Post by mjta on 2008-12-04
It is indeed an ubuntu partition.

---

