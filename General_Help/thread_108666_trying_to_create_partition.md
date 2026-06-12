---
title: "trying to create partition"
date: 2005-12-26
forum: General Help
---

### Post by eyebrowman92 on 2005-12-26
on my hda theres a windows partition with an nfts filesystem and im trying to shrink it so i can install ubuntu. problem is after i resize it, make a new partition, when i press apply it says a device was busy. what does this mean?

---

### Post by zoiks on 2005-12-26
Usually that means the device is mounted or someone has open files on it.  Make sure it's umounted and close any windows/apps that have opened files or directories on it.

---

