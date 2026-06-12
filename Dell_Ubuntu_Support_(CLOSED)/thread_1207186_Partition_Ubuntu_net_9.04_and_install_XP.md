---
title: "Partition Ubuntu net 9.04 and install XP"
date: 2009-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brie987 on 2009-07-07
Hello Im not sure if this is the right thread but Im going for it anyway.  I have a Dell mini 9 with Ubuntu 9.04.  I love it.  I do however need to install a lite version of XP for just a couple of programs one of which is a program to tether my Google G1 phone to Mini 9 so I can use it as a wireless modem when I am not around a wifi. With Ubuntu already installed how do I create a partition on my SSD drive (64gig) and install XP lite on?
Thank you so much for all your help and insight.  Sorry if this is posted in the wrong thread.

---

### Post by ugm6hr on 2009-07-08
Repartitioning and installing a new OS is not something I would recommend for beginners.

However, the following would be a good strategy:
1. Boot using a LiveUSB of Ubuntu
2. Use GParted (Partition Editor) to shrink existing partition, and create a new FAT partition for XP (needs to be a primary partition)
3. Reboot using XP installation media (presumably CD in an external drive)
4. Use XP installation wizard to reformat the pre-created FAT partition (ensure it does not format Ubuntu partition) - your choice FAT or NTFS
5. Continue to install XP
6. Reboot using LiveUSB of Ubuntu
7. Rewrite GRUB to the SSD boot sector
8. Reboot as normal, and you should have a working dual boot.

If any of these steps makes no sense whatsoever, I would suggest asking someone who knows what they are doing to sort this for you.  Or ask again here.

Beware: Installing an OS and repartitioning can lose all your data, even if you don't make any mistakes.  Hence, BACKUP everything important first.

---

### Post by mikewhatever on 2009-07-08
I suppose you can use a live cd/usb Ubuntu, shrink one of the existing partitions and use the unallocated space to install the other OS. The reason to use live media and not the existing installation is to make sure the partition is not mounted. The program to use for managing partition is gparted, which, when installed, is located under System->Admin->Partition Manager.

---

