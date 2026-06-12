---
title: "[SOLVED] Testing Disk Drive Thru-Put"
date: 2007-07-03
forum: Desktop Environments
---

### Post by fjgaude on 2007-07-03
Anybody willing to recommend a program that can test the thru-put of disk drives? You know to determine their MB/second transfer rate?

frank

---

### Post by logos34 on 2007-07-03
(for ide drives):

**sudo hdparm -tT /dev/hda**

---

### Post by fjgaude on 2007-07-03
> **logos34 said:**
> (for ide drives):

**sudo hdparm -tT /dev/hda**

Thanks, I have used such on a 2-disk RAID0 set of mine and get 81.73 MB/sec for buffered read.

On a single disk is get 59.59 MB/sec.

Hmmm... my software RAID is not too much better than a single drive. 1.33 times faster, 33%; had hoped for something like 90% faster with two disks.

Will have to think about it.

Thanks again for the tip.

frank

---

