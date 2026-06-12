---
title: "IDE Card"
date: 2009-04-06
forum: General Help
---

### Post by Raptor45 on 2009-04-06
After some troubleshooting, it seems the IDE controller on my motherboard has died. I don't have any readily available SATA drives, so I'm looking to buy a cheap PCI card.

Will any of these work with Ubuntu? I don't need RAID.

[http://www.newegg.com/Product/...&bop=And&Order=PRICE](http://www.newegg.com/Product/...&bop=And&Order=PRICE)

---

### Post by cariboo on 2009-04-06
Your link doesn't work. :(

Jim

---

### Post by kpoole on 2009-04-06
I cannot speak for all IDE cards but I do know that my old Promise Ultra 100 IDE expansion card works.  The only caveat is that, depending on the particular version, 8.04, 8.10, 9.04, the drives may not map to the drive letters you expect.  Use the partition UUID numbers to identify the partitions in the /etc/fstab.

(I had a machine with a bunch of smaller drives in it for file backups, 7 hard drives and one CD writer.)

---

