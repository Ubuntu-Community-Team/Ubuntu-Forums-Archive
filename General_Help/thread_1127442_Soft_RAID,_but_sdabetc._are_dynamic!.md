---
title: "Soft RAID, but sda/b/etc. are dynamic!"
date: 2009-04-16
forum: General Help
---

### Post by AboveTheLogic on 2009-04-16
Hello everyone.

I have the following configuration. My board has 1 IDE port and 6 SATA ports.

IDE:
Master: 160GB System Drive
Slave: 750GB Data Drive

SATA1: DVD/RW
SATA2: 1TB Data Drive
SATA3: 1TB Data Drive
SATA4: 1TB Data Drive

Right now, the IDE Master and Slave are sda and sdb respectively. The 1TB drives are sdc, sdd, and sde. 

Sometimes when I reboot, the SATA drives are sda, sdb, sdc; with the IDE drives as sdd and sde. Matter of fact, earlier this morning thats how it was before I rebooted.

I used mount manager to create the fstab file so that the UUID is used to mount the drives instead of the /dev/sd* path. This has been successful so far, but now I want to create a software RAID by putting 2 of the 1TB drives in a mirror RAID, and I noticed that mdadm needs the /dev/sd* path, and I'm concerned with my RAID failing after a reboot and I very much want to prevent loss of data (the whole reason why I want the RAID).

Anyone have any ideas? I'm wondering if I can use the UUID somehow in the mdadm --create command, but haven't tried it yet (I'm very new to RAIDs, not new to linux).

Thanks!

---

### Post by fjgaude on 2009-04-18
Well, fear not, for **mdadm** uses a special UUID to assemble an arry, doesn't use a drives name.

Mount the array using its /deb/md0 name. No need to use mount UUIDs here, but you do with the boot and swap partitions.

---

### Post by AboveTheLogic on 2009-04-21
but that's a UUID for mounting the array itself, right?

the array points to the 2 drives, /dev/sda1 and /dev/sda2, and if those are changed, I think the raid will fail

anyways, I think I have it figured out, I changed my SATA mode in the BIOS from IDE to ACHI (i think) and it seems to have fixed the problem

---

### Post by fjgaude on 2009-04-21
No, the **mdadm** UUID created by it is the same for each drive in the array. This UUID is not the one that is used to mount drives or the array.

Glad you have things working again.

---

### Post by AboveTheLogic on 2009-04-21
hmm

that's interesting

well I never really did get the RAID working properly, I ended up with some superblock problems and I decided to just scrap the RAID idea and just do incremental backups to one of the drives every night (not a big deal if something is out of date by a day)

but, at least the drives /dev paths are constant, haha

thanks for the input

---

