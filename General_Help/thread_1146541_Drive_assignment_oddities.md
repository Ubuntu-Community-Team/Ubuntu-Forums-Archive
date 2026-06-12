---
title: "Drive assignment oddities"
date: 2009-05-02
forum: General Help
---

### Post by dwasifar on 2009-05-02
I've encountered something a bit weird with drive assignments in my desktop system.

The machine is built on a Gigabyte GA-EP45-UD3P MB with 8 onboard SATA ports.  Typically I have three drives connected: the main system drive, a storage drive, and an internal spare, which generally contains the system as it was before the last Ubuntu upgrade (e.g. if I am running 8.10, the internal spare contains 8.04).  

When I first built this system and set up the drives, I found the storage drive at /dev/sdc rather than /dev/sdb where I expected it.  I thought I had just mixed something up, revised /etc/fstab to accommodate it, and moved on.  But today I found it's more than that.  I cloned the main drive to the internal spare using dd, in preparation for a Jaunty upgrade, then switched the SATA0 cable to that drive and left the original drive unconnected.  This caused the system to fail on boot, reporting it couldn't find the storage drive, which I hadn't touched.  About 15 minutes of cable swapping and rebooting ensued while I tried to figure out the problem, which turned out to be that the drives are assigned /dev/sd[x] inconsistently, depending on how many drives are attached.

Specifically, I found that if I have two drives attached, they go like this:

SATA0: /dev/sda
SATA1: /dev/sdb

But if three drives are attached, they map like this:

SATA0: /dev/sda
SATA1: /dev/sdc
SATA2: /dev/sdb

So whether SATA1 is /dev/sdb or /dev/sdc depends on whether there's a drive at SATA2 or not.

This seems weird.  I'm sure I've never seen this with any previous MB or system.  Can anyone explain what is going on?

---

### Post by Yellow Pasque on 2009-05-02
I've seen plenty of reports of drive letter swapping and experienced it myself, so it's not uncommon. IIRC, there's a way to force udev to assign drive letters consistently (wish I had a link to give you).

Actually, programs shouldn't assume drive lettering (and neither should you). Identify your disks before using drive letters and use UUID's in /etc/fstab where possible.
```
sudo fdisk -l
blkid
```

---

### Post by dwasifar on 2009-05-02
I have been burnt by UUID's before.  You remember I described cloning my HD by using dd, right?  This results in two drives with the same UUID.  I didn't realize that for a while, until one day I accidentally cloned an old configuration over a new one because I was mistaken about which of the two the system was booting from.  Since then I have always edited fstab and menu.lst to use drive letters instead of UUIDs.

Is it even possible to use UUIDs in dd?

---

