---
title: "How to partition Inspiron 1525 for dual boot"
date: 2009-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tommyp on 2009-12-31
I've got an Inspiron 1525 laptop currently running Vista, which I would like to dual-boot with Ubuntu (not using Wubi - a real install).  The partitions are currently:

71MB (I assume this is a boot partition)
Recovery partition
Vista partition
2.5GB partition (is this the mediadirect volume?)

What is the best way to dual boot?  All of my previous installs seem to have needed both an ubuntu and swap partition. Since I am limited to 4 partions, does this mean I have to delete both the Media direct(fine with that) and the Recovery(don't know if it's okay to delete it)?

Thanks

---

### Post by mikewhatever on 2010-01-01
Since Ubuntu partitions don't have to be primary, you only have to delete one partition. Regards, and good luck.

---

### Post by bobcollard on 2010-01-01
> **tommyp said:**
> I've got an Inspiron 1525 laptop currently running Vista, which I would like to dual-boot with Ubuntu (not using Wubi - a real install).  The partitions are currently:

71MB (I assume this is a boot partition)
Recovery partition
Vista partition
2.5GB partition (is this the mediadirect volume?)

What is the best way to dual boot?  All of my previous installs seem to have needed both an ubuntu and swap partition. Since I am limited to 4 partions, does this mean I have to delete both the Media direct(fine with that) and the Recovery(don't know if it's okay to delete it)?

Thanks

So far it looks like you have not tried to install Ubuntu.  When you do install it there will be a choice to either install Ubuntu "Side by side" with Vista or use the entire disk.  The other choice is for you to do the partitioning and if you have no idea what you are doing don't even attempt it.  Choose "Side by Side" and the installer will do the partitioning for you.  After a restart you will find a choice in what is called (Grub) to run Vista or Ubuntu.

---

