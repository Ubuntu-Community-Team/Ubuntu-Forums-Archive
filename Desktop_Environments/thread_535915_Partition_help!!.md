---
title: "Partition help!!"
date: 2007-08-27
forum: Desktop Environments
---

### Post by rkakkar on 2007-08-27
I have run into a bit of a problem here. I have 3 partitions on my machine - the main / (ext3), swap and data (fat32). I have run out of space on my / (ext3) parition. So I need to pull out an empty chunk from my fat32 partition and merge ti (after converting) with my main / parition. How can I go about doign this?

---

### Post by jnorthr on 2007-08-27
you may find it easier to just delete some of your old log files. Look in /var/log/ and it's sub-directories for old log and spool printer files you can archive or remove. That may be enough to get you over this problem, otherwise you might not be able to make / root bigger with swap partition in the way. You always need a swap partition. Is it possible to remove your current swap partition and add that to root, then take some space from the end of the fat32 as the swap partition ?

---

