---
title: "Reinstall Ubuntu 8.10 Without Formating Partition"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abscess on 2009-01-21
Hi again

I wonder.. Is it possible to reinstall Ubuntu 8.10 without formating the partition?

Booting from CD, choosing "manual partitioning", mount the existing partition and GO!

Will the home directory still be intact? Will all of my folders at root level still be intact? Will the installed system be a "clean" install?

---

### Post by vanadium on 2009-01-21
A clean install involves wiping the system files. If you have your /home on a separate partition, then you can have the new installation use the old /home directory. If you do not have /home on a separate partition, there are some options:

Option 1: If you are enough technically savvy, you could first create a /home on a separate partition. A thorough guide is here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). After that, you can reinstall and reuse the home partition.

Option 2: Copy your /home to another ext3 partition and put it back after installation. Copying the /home is not trivial as suggested in the post I linked to. A complicated command is mentioned, looking like

```

find . -depth -print0 | cpio --null --sparse -pvd /new/

```

A far more easy approach is to backup your user date (something you should do anyway), then have a default, clean re-install, reconfigure your system, and restore your data. It depends on your skills. If your data are safe, it does not harm to try the more complicated solution first: you will learn.

---

