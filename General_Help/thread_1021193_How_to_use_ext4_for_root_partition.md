---
title: "How to use ext4 for root partition ?"
date: 2008-12-25
forum: General Help
---

### Post by tinkywinky on 2008-12-25
Hi,

I want to use ext4 instead of ext3 for my root partition. Is it sufficient to replace "ext3" by "ext4dev" in /etc/ftab :

```
UUID=4ed47d43-6464-4a7d-afe4-dbdd5a484078 /               ext3    noatime,nodiratime,relatime,errors=remount-ro,data=writeback  0       1
```
=>
```
UUID=4ed47d43-6464-4a7d-afe4-dbdd5a484078 /               ext4dev    noatime,nodiratime,relatime,errors=remount-ro,data=writeback  0       1
```

Will it works ? (I'm on 8.10).

Thanks !

---

### Post by SPr on 2008-12-25
You'll have to format the root partition to ext4 and reinstall Ubuntu.

---

### Post by tinkywinky on 2008-12-25
Why do I have to reformat ? I've already mounted ext3 partitions as ext4 in the past, without problem...

---

### Post by SPr on 2008-12-25
You formatted the HDD as ext3 when you installed Ubuntu so surely you will have to format it to ext4 to use ext4. Because Ubuntu will mount an ext3 file system as ext4 (which sounds strange to me) doesn't mean that the ext3 file system will be altered in any way - unless I'm seriously mistaken.

---

### Post by zvacet on 2008-12-25
Every change of format will erase existing patition.What are you trying to do is **format **your partition and that will lead to data lost.

---

### Post by obsrv on 2008-12-25
I don't recommend using Ext4 as root partition because it is still DEVELOPMENT as far as I know. When I used Ext4 in ArchLinux I had a few problems with it. What for you need Ext4?

---

### Post by sdennie on 2008-12-25
You can change an ext3 partition to ext4 without reformatting it but, existing files that are stored on the disk in ext3 format (so, not using extents) will remain that way and you will essentially have a mixed ext3/ext4 partition.  

There is not a single tool that will magically convert ext3 to ext4 and I really don't recommend you mount root as ext4 unless you are running kernel 2.6.28 and are willing to potentially break low level, important utilities that you need to do ext4 "correctly".  I just got done switching my Hardy machine from ext3 to ext4 (including root as full ext4) because I was going to write a guide on how to do but, now I think the best guide would be, "Wait until Ubuntu natively supports it".

---

### Post by tinkywinky on 2008-12-26
OK thanks for your answers! Then I'll wait until Ubuntu supports it.

---

### Post by LastJudge on 2008-12-30
if you want to change from ext3 to ext4, just type:
```
$ tune2fs -O extents -E test_fs /dev/DEV
```

but the old files will remain unchanged, only the new files will be ext4...
and you won't be able to mount the partition as ext3 anymore

so I think we should still wait...

---

### Post by Nepherte on 2008-12-30
> **obsrv said:**
> I don't recommend using Ext4 as root partition because it is still DEVELOPMENT as far as I know. When I used Ext4 in ArchLinux I had a few problems with it. What for you need Ext4?
With the release of 2.6.28 ext4 has been marked as stable. You can get it to work with 2.6.27 as well, but I wouldn't recommend it.

---

