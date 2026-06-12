---
title: "Remove UDF partition"
date: 2009-04-29
forum: General Help
---

### Post by ashughes on 2009-04-29
I have a USB hard drive with a 36 MB UDF partition loaded by the manufacturer.  I'd like to reclaim this space, unfortunately, I have yet to find a tool that will let me remove this partition.  It seems that gparted does not recognize it and I cannot seem to mount it with write permission in Ubuntu.

---

### Post by dcstar on 2009-04-29
> **ashughes said:**
> I have a USB hard drive with a 36 MB UDF partition loaded by the manufacturer.  I'd like to reclaim this space, unfortunately, I have yet to find a tool that will let me remove this partition.  It seems that gparted does not recognize it and I cannot seem to mount it with write permission in Ubuntu.

gparted will show you all partitions on a device, post a screenshot.

---

### Post by ashughes on 2009-04-29
Gparted does not show the udf partition.  The way the device is mapped in Ubuntu, the ntfs partition is /dev/sdb1 and the udf partition is /dev/sr1.

I can take a screenshot of gparted, but you will only see /dev/sdb1.

---

### Post by dcstar on 2009-04-29
> **ashughes said:**
> Gparted does not show the udf partition.  The way the device is mapped in Ubuntu, the ntfs partition is /dev/sdb1 and the udf partition is /dev/sr1.

I can take a screenshot of gparted, but you will only see /dev/sdb1.

cfdisk will allow you to delete partition tables.

---

### Post by ashughes on 2009-04-29
I can't see how cfdisk allows me to delete the partition table.  I can modify partitions with it, but not the tables.

---

### Post by dcstar on 2009-04-29
> **ashughes said:**
> I can't see how cfdisk allows me to delete the partition table.  I can modify partitions with it, but not the tables.

Then use the Create Partition Table feature in the Partition Editor.

---

### Post by ashughes on 2009-04-30
I have tried this.  It just errors out.

---

### Post by dcstar on 2009-04-30
> **ashughes said:**
> I have tried this.  It just errors out.

Then the device itself has been designed not to allow this partition structure to be altered.

---

### Post by ashughes on 2009-04-30
I gave up...

I went out and bought an enclosure and OEM drive separately.  This solves the problem for me.  I'll just have to sell the original drive to someone who uses Windows.  Off to Craigslist I go...

---

### Post by Youresorock on 2009-06-26
You may have craigslisted the drive already, but have you tried using dd to write zeros to the entire drive?  that would wipe out any partitions nicely.

---

