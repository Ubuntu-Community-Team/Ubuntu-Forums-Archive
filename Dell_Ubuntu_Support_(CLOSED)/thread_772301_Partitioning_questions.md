---
title: "Partitioning questions"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LeeM on 2008-04-28
Hi! I have a brand new Dell Vostro 1400 which I want to dual boot (existing XP Home and Ubuntu 8.04). My questions are

1. When I look at the existing partions (using QParted on Knoppix CD), I see an extended partition of 2.5GB (0.7GB used), fat32 format, labelled "DelMD3play". Anyone know what that might be, and if I can safely kill it?

2. Is there any disadvantage to putting linux on the extended (04) partition, rather than on the main partitions (01 - 03)?

Thanks!:)

---

### Post by gekkio on 2008-04-28
1.
Those kind of partitions are usually related to the recovery of the preinstalled Windows XP (or Vista) system.
I had an Acer laptop once which had a similar partition. I completely wiped out the hard drive, but I was still able to restore Windows XP installation (because I was selling the laptop) using the recovery DVD.
I'm pretty sure it's safe to kill it if you have a recovery DVD. On my Acer the machine burned the DVD on the first boot, but it might be different on other machines.
**Summary**: If you need the space, go ahead, but there's a chance you'll mess up your XP recovery possibility.

2.
Nope (as far as I know). Remember that unless you use LVM, you'll want at least two partitions anyway (swap + root), so when using an extended partition at least you won't run out of partitions.

Just remember to **first install Windows** then Ubuntu if you want a dual-boot setup. I didn't, and I almost died of frustration with my Dell D630 when Windows XP wouldn't install (for some ridicolous reason Windows wants to be installed first. It's somehow related to the MBR of the hard disk, can't remember exact details). :)

---

### Post by neptho on 2008-04-28
MD3 stands for 'Media Direct 3'.  That's where the 'one button DVD player' is stored.  Do NOT remove the FAT16 partition, this is the system's diagnostic partition.  Everything else is safe to kill, if you truly want to.

There used to be technical reasons to need/keep Linux in a primary partition, but with the death of PATA, they're highly superficial.

---

