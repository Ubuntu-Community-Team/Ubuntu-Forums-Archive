---
title: "LVM2, combined two harddrives(volume group), and it shows 29GB as being used?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by statictonic on 2006-08-02
I just bought two 320GB sata seagate hdd, anyways combined they show up as 596GB in LVM2, however when i check how much space is available I only see 557GB free.  I tried both ext2 and ext3 both with the same results.  Any idea what could cause this?

Also one other question about combining drives in LVM2, I have a drive currently formatted as fat32 with about 400gb of data on it, I need to merge it with the other two drives, I'm going to guess it might been to be reformated to EXT3 like the other two, but when ever I add a drive do I need to reformat all the drives together or just the drive I'm adding?

---

### Post by mlind on 2006-08-02
Could post the output of **vgs** and **lvs**

---

### Post by statictonic on 2006-08-02
> **mlind said:**
> Could post the output of **vgs** and **lvs**

Where can I get that output?  I'm actually using a GUI to set it up right now.

---

### Post by mlind on 2006-08-02
> **statictonic said:**
> Where can I get that output?  I'm actually using a GUI to set it up right now.

You type it on a terminal. I've never used GUI to setup LVM, so I can't help you there.

When you add a new drive to LVM (as PV), the only formatting you need to do is to mark it as LVM (8e). Backup your data though before assigning drive as LVM.
You later on assign filesystem type to LV (basically a dynamically sized partition).

Just think LVM as a pool of space that you can allocate as filesystems.
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

---

