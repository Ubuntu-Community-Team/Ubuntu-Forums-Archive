---
title: "problem with partimage"
date: 2009-01-15
forum: General Help
---

### Post by davidtuti on 2009-01-15
Hi,

I would like to create an image from my linux partition ext3 and I would like to save in other partition that it's in ntfs. I use the systemrescueCD and partimage. I do:

When I boot with sysemrescueCD I do:
mkdir /mnt/temp
mount -w /dev/sdb5 /mnt/temp

But the partition ntfs mounts with read-only and I can't save the image in this localization.

Could you help me?
Many thanks and sorry for my english!

---

### Post by Titan8990 on 2009-01-15
You should read the MOTD for systemresecue...


try this:

ntfs-3g /dev/sdb5 /mnt/temp


The -w flag for mount is completely unnecessary as mount uses the -w flag by default.

---

