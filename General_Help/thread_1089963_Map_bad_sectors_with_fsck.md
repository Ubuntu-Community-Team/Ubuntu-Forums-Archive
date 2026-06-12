---
title: "Map bad sectors with fsck?"
date: 2009-03-07
forum: General Help
---

### Post by adcurtin on 2009-03-07
My neighbor has a hard drive with bad sectors on it. He already replaced it, and now he wants to install Ubuntu on the hard drive with bad sectors. How can I find and map the bad sectors so the file system doesn't use them (similar to a non quick format in the XP installer, but I want the file system to be ext3). There's nothing on the drive, it can be formatted, and whatever needs to be done will most likely need to be done with a live cd, which isn't a problem.

tl;dr
how to use fsck to map bad sectors so an ext3 file system will ignore them?

Thanks,
Andy

---

### Post by brian_p on 2009-03-07
> **adcurtin said:**
> 

how to use fsck to map bad sectors so an ext3 file system will ignore them?

```
man fsck.ext2
```

The -c option

Also

```
man badblocks
```

---

### Post by tgalati4 on 2009-03-07
sudo fsck -cc /dev/sdb1

---

