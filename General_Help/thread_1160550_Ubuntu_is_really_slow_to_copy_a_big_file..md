---
title: "Ubuntu is really slow to copy a big file."
date: 2009-05-15
forum: General Help
---

### Post by Envergure on 2009-05-15
I am currently copying a 6.7GB archive onto my flash drive, and it's only running at 1.2MB/s and getting slower.  It doesn't go that slow for smaller files (usually about 40MB/s).

Also, my CPU is running at 100% of "IOWait" usage but the computer isn't heating up because the CPU is running on low-power 1GHz mode (it can scale up to 1.83GHz).  Whatever's using all that computing power doesn't show up in System Monitor.  It's at the lowest priority.

---

### Post by Happy_Man on 2009-05-15
Is the flash drive formatted NTFS or FAT32?

---

### Post by lloyd_b on 2009-05-15
> **Envergure said:**
> I am currently copying a 6.7GB archive onto my flash drive, and it's only running at 1.2MB/s and getting slower.  It doesn't go that slow for smaller files (usually about 40MB/s).

Also, my CPU is running at 100% of "IOWait" usage but the computer isn't heating up because the CPU is running on low-power 1GHz mode (it can scale up to 1.83GHz).  Whatever's using all that computing power doesn't show up in System Monitor.  It's at the lowest priority.

"IOWait" means that the CPU is idling, waiting for some for type of I/O (Input/Output).  In other words, it's stuck waiting on either the flash drive or your HD.  I'd suspect the flash drive, of course...

Lloyd B.

---

