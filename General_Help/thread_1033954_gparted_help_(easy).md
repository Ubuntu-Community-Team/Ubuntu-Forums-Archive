---
title: "gparted help (easy)"
date: 2009-01-07
forum: General Help
---

### Post by sPiN1 on 2009-01-07
i have way to much junk in my gparted (i think) 
i have partition /dev/sda1 with filesystem ntfs size 125.35 gb
/dev/sda2 ext3 100.92gb
/dev/sda4 extended 6.56gb
/dev/sda6 ext3 3.68gb
/dev/sda5 linux-swap 2.98gb

which can i delete i all i want is one linux partition and one windows partition i don't want to delete something i need though

---

### Post by dcstar on 2009-01-07
> **sPiN1 said:**
> i have way to much junk in my gparted (i think) 
i have partition /dev/sda1 with filesystem ntfs size 125.35 gb
/dev/sda2 ext3 100.92gb
/dev/sda4 extended 6.56gb
/dev/sda6 ext3 3.68gb
/dev/sda5 linux-swap 2.98gb

which can i delete i all i want is one linux partition and one windows partition i don't want to delete something i need though

gparted is a program that allows you to work on partitions, it is not a "thing" that can contain junk.

Delete the sda5 (swap) and sda6 partitions, then you can delete the sda4 extended partition and increase the size of your sda2 partition into most the free space. Leave a bit at the end for creating a new swap partition (you probably don't need 3G).

Do this with the Partition Manager booting off a Live CD.

You will need to manually edit your /etc/fstab file once this is all done as UUIDs will have changed and other entries may have to be removed.

---

