---
title: "Backup mbr and superblock/grub/important info"
date: 2011-01-15
forum: Desktop Environments
---

### Post by amsterdamharu on 2011-01-15
Right now I use dd to backup mbr and the first 512 bytes of every partiton.

```
dd if=/dev/sd? of=sd?.bin bs=512 count=1
```

That would take care of the partition tables and grub in the mbr, but what about the superblock, the stuff that XP stores and the superblock?

```
dd if=/dev/sd?1 of=sd?1.bin bs=512 count=1
```

Is it save to assume that if grub was on sd?1 it is backed up? 
Does it backup the superblock so if some bug or power failure makes the partition unmountable because of bad superblock it can be fixed by copying back the first 512 bytes?

I am of course not changing partition size or type of filesystem and not messing around with grub.

---

### Post by amsterdamharu on 2011-01-16
Bump

---

