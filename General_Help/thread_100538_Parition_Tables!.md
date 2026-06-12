---
title: "Parition Tables!?"
date: 2005-12-07
forum: General Help
---

### Post by cdhotfire on 2005-12-07
Well I was trying to make an extended drive in gparted, then suddendly instead it shows unpartitioned space? Now it says I says I have no partitions, and if I make new partition it will erease all my drive?

Also if I do "fdisk -l" shows nothing, only if I look under partitions by "cat /proc/partitions" it shows my partitions.

I was reading some things on net and they lead to corrupted partition table. Any ideas on how to get my drive back in shape? :rolleyes:

---

### Post by wounded on 2005-12-07
[QUOTE=cdhotfire]Well I was trying to make an extended drive in gparted, then suddendly instead it shows unpartitioned space? Now it says I says I have no partitions, and if I make new partition it will erease all my drive?

Also if I do "fdisk -l" shows nothing, only if I look under partitions by "cat /proc/partitions" it shows my partitions.

I was reading some things on net and they lead to corrupted partition table. Any ideas on how to get my drive back in shape? :rolleyes:[/QUOTE]
I haven't used gparted yet (Haven't needed to) but I can help you with the fdisk. "fdisk -l" won't give you any output, "sudo fdisk -l" should display your current partition information though. Maybe that will help you (Or help us?) with your partitioning problem.

---

### Post by cdhotfire on 2005-12-16
I ended up just deleting everything, and remade the partition tables.  By the way sudo fdisk, did not show anything.  I tried bchunk to try to find the start adn end cylinders but I didnt want to dedicate that much time.:rolleyes:

---

