---
title: "Resizing partititions"
date: 2006-01-10
forum: General Help
---

### Post by ossi on 2006-01-10
Hi!

I wanted to ask if it is anyhow possible to resize partititions and move one part to another exisiting partition. I got the following partitions:

- Windows 15 GB
- Ubuntu 10 GB
- Data 45 GB
- Swap

Now I would like to make the Windows partition smaller (since I dont really need it :cool: ) and give the free space to the existing Ubuntu Partition. Is there a way or do I have to set up the partitions completely new?

---

### Post by canadianwriterman on 2006-01-10
A good partitioning tool, like qtparted, will do the job nicely.

---

### Post by TheForumTroll on 2006-01-10
Or the gnome version, gparted.

---

### Post by az on 2006-01-10
You need to run any of those from a live cd since you cannot resize any partition on a disk with mounted partitions on it.  You need to unmount your swap if you run from the ubuntu live cd for this reason.

---

