---
title: "A little more Partimage help - I've almost got it!"
date: 2009-05-05
forum: General Help
---

### Post by crispeto on 2009-05-05
So here's the deal. I think I've almost learned how to run this program but I get all the way to letting it clone but it always tells me that there is only 1 gig on the drive. After it uses up the 1 gig, it states that there is no more room on the destination. It's a Western Digital drive with two partitions. The drive I'm trying to image my Ubuntu HD to has 30 gigs and there's nothing on it. I've formatted to NTFS, and then, Fat32, and also ext3 and none of them work. They all only register as just less than one gig of space and then I run out of room. When the disk is mounted on Ubuntu, it calls itself disk-1. What am I doing wrong? I'd really like to image my drive. Thanks.

---

### Post by dcstar on 2009-05-05
> **crispeto said:**
> So here's the deal. I think I've almost learned how to run this program but I get all the way to letting it clone but it always tells me that there is only 1 gig on the drive. After it uses up the 1 gig, it states that there is no more room on the destination. It's a Western Digital drive with two partitions. The drive I'm trying to image my Ubuntu HD to has 30 gigs and there's nothing on it. I've formatted to NTFS, and then, Fat32, and also ext3 and none of them work. They all only register as just less than one gig of space and then I run out of room. When the disk is mounted on Ubuntu, it calls itself disk-1. What am I doing wrong? I'd really like to image my drive. Thanks.

Partimage copies to a file on a filesystem, you must already have a mounted filesystem with space for the destination file.

---

### Post by crispeto on 2009-05-05
So, how do I do that? I have no idea how to do that.

---

