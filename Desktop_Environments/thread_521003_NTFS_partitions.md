---
title: "NTFS partitions"
date: 2007-08-08
forum: Desktop Environments
---

### Post by alohanema on 2007-08-08
I've got two NTFS partitions and when I mount them, I just can read, I can't write something into these partitions. Please tell me!
Thanks

---

### Post by merlinus on 2007-08-08
```

sudo apt-get install ntfs-3g ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes, and restart.

-merlin

---

