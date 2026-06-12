---
title: "DD only used?"
date: 2009-05-16
forum: General Help
---

### Post by kevin11951 on 2009-05-16
Is it possible to use dd to copy only the used parts of a hdd?

---

### Post by MaxIBoy on 2009-05-16
No. dd copies over raw data.

What you want is the "cp" command, which only copies over the useful data without the empty space.

EDIT: Unless you're talking about copying only a specific partition, in which case you can use dd on the partition. So if you have un-partitioned space on your hard drive, you can skip it. But you'd still be copying all the unused space in the partition.

---

### Post by cariboo on 2009-05-16
Partimage functions the same as dd, only it doesn't clone the empty space. Partimage is in the repositories.

---

### Post by kevin11951 on 2009-05-16
> **cariboo907 said:**
> Partimage functions the same as dd, only it doesn't clone the empty space. Partimage is in the repositories.

can you mount a partimage image after cloning?

---

