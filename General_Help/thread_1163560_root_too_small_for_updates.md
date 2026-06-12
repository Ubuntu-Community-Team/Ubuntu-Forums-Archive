---
title: "root too small for updates"
date: 2009-05-18
forum: General Help
---

### Post by hdrider on 2009-05-18
How do I enlarge the root \ so that I don't get error msg when updating. I have an 8 gib 
ext3 partition that is not mounted. If I mount it, it shows up as lost&found? Can anyone
give me direction? Thanks in advance. How can I add this partition to the root or mount
this partition as the root and copy from the previous \ ?

---

### Post by Miljet on 2009-05-18
Please open a terminal and post the output of

```
sudo fdisk -l
```

That way we can get a better understanding of your partitions.

---

