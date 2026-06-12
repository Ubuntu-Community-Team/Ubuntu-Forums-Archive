---
title: "Longer boot-up after reformating partition"
date: 2006-03-15
forum: Desktop Environments
---

### Post by banjobacon on 2006-03-15
I have 150 gig hard drive that used to be mounted as an NTFS partition. I later formated it as reiserfs and used it as my /home partition.

Ever since reformating it, my computer stalls for a little while when booting. This happens during the following steps: "Checking all filesystems" and "Mounting filesystems". 

Does it simply take more time to deal with reiserfs than with NTFS, or is something wrong?

---

### Post by dickohead on 2006-03-15
Not that I'm aware of, but you are now actively using that partition, not just reading it, you're mounting it to your tree structure.

Are all your linux partitions (excluding swap) reiserfs?

---

### Post by banjobacon on 2006-03-15
Yes, my root partition is also reiserfs.

---

