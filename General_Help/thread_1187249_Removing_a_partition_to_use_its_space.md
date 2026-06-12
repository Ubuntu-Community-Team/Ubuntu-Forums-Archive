---
title: "Removing a partition to use its space"
date: 2009-06-14
forum: General Help
---

### Post by Hoodline on 2009-06-14
I have windows and unbuntu installed on the same hard drive but i cant boot into windows no more how can i remove windows and use its space for ubuntu

---

### Post by CatKiller on 2009-06-14
Use GParted. It's on the install cd as "Partition Editor." Remove your Windows partition and then select the partition that you want to expand. Select Resize/Move and increase the size of your Ubuntu partition. You may find that you need to change GRUB's menu.lst to point to the correct partition for it to boot - it's probably a case of changing (hd0,1) to (hd0,0). [Here]("http://linuxmint.com/wiki/index.php/How_to_repair_your_grub#Locate_a_boot_folder.2Fpartition_to_use") are some instructions if you have difficulty.

Otherwise, you could just format that partition to ext3 and use that partition for something else. A data partition, or a [separate /home partition]("http://www.psychocats.net/ubuntu/separatehome"), perhaps.

---

