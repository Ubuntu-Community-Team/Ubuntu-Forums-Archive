---
title: "partitioning"
date: 2007-07-15
forum: Dell  Ubuntu Support
---

### Post by Ryuusen on 2007-07-15
I've got an 80gb or so hdd on my dell inspiron 6400. it's partitioned into a 60gb and a 20gb partition. when i go to set up a swap partition on the 20, w/e wasn't used in the swap is labelled as unusable. if i try to set up some of that 20 for the actual OS, the remaining is also listed as unusable. help!

---

### Post by MyR on 2007-07-15
you need three partitions, the 60gb one, a 18gb ext3 for linux, and 2gb swap (or more if you have more than 2gb RAM).

---

### Post by Ryuusen on 2007-07-15
can the ubuntu partitioner do that?

---

### Post by MyR on 2007-07-15
yep

---

### Post by Ryuusen on 2007-07-16
how would i go about doing that?

---

### Post by Ryuusen on 2007-07-16
so i figured out how to set up the partitions i need, but i'm only allowed 4 partitions. would it be safe to delete the recovery partition to free up one of the four primaries?

---

### Post by neptho on 2007-07-16
It is safe to delete if you feel you'll never need it again - but, you can create an 'extended' partition instead of a 'primary' partition, and create subpartitions under that.

So,

```
sda1 /
sda2 swap
sda3 /boot
sda4 /usr
```

Could become:

```
sda1 /boot
sda2 swap
sda3 - extended
   sda5 /var
   sda6 /home
sda4 /usr
```

There's plenty more documentation on how to do this, and discern what the differences are.  Essentially, there are only 4 allowed primary partitions due to old reasoning, but you can 'cut them up' into smaller slices.. which isn't really different than a BSD diskslice.

---

### Post by strabes on 2007-07-17
To answer your question, yes it is safe to delete the recovery partition. It's pretty useless if you back up your files and have a copy of the operating system you use.

---

