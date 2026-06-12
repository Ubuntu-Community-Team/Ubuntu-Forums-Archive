---
title: "Dual-boot problems"
date: 2009-01-25
forum: General Help
---

### Post by unleashed26 on 2009-01-25
Sorry if this thread is in the wrong place.

Earlier today I decided to give Ubuntu a try (I use Windows Vista Home Premium) so I partitioned the hard drive, downloaded Ubuntu and installed it on the partition.

The problem is that I'd like to boot back into Windows Vista now but I don't know how. Any advice would be appreciated a lot.

Thanks :)

---

### Post by Shazaam on 2009-01-25
When your pc boots and you see "hit your ESC key" what happens when you click that key? Do you see a list of kernels/operating systems? And if you do see them what hapens when you choose the Windows one and click enter?

---

### Post by unleashed26 on 2009-01-25
Ubuntu, ubuntu recovery mode and ubuntu memory test or something similar. No Windows Vista apparent.

---

### Post by mb_webguy on 2009-01-25
I hate to be the one to suggest this, but are you absolutely sure you didn't install Ubuntu over your Windows installation?

---

### Post by unleashed26 on 2009-01-25
I'm pretty sure I didn't on purpose.

What I did was first partition the hard drive with Vista's built in manager and then attempted to install Ubuntu. It asked me where I wanted to install it but I couldn't get it to install onto the partition I had made (my fault, I didn't look hard enough). So I went back into Vista and merged both partitions again and then partitioned the hard drive using the Ubuntu installer.

I've had a look at the current partitions on the drive; what I see is the partition I made using the installer (about 15 GB) and the unallocated free space.

---

### Post by mb_webguy on 2009-01-25
Do you see the Vista partition?

---

### Post by unleashed26 on 2009-01-25
No I did not, nor did I see its recovery partition that came with the laptop  in place of a Vista installation DVD.

---

### Post by mb_webguy on 2009-01-25
Well, I have some good news and some bad news.  The good news is that you *may* very well have installed Ubuntu over Windows.  The bad news is that I lied about it being good news (assuming you wanted to keep Windows).  Partitioners should always be used with caution, and only after making backups of everything you want to keep.

Can you open the terminal and post the output of "sudo fdisk -l"?

---

### Post by unleashed26 on 2009-01-25
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x402155d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux

---

### Post by mb_webguy on 2009-01-25
Yep, I'd say that you installed over Windows.  For future reference, you need to do the Manual installation when you get to the partitioning part of the installer, not Guided.

I do find it odd, though, that fdisk isn't showing a swap partition...  Hrm...

---

### Post by unleashed26 on 2009-01-25
I did select manual. I clicked on create new partition table and then new partition. It asked if I wanted to create a swap partition to use if there isn't enough physical memory - I assumed there was enough so I skipped it.

---

### Post by mb_webguy on 2009-01-25
...

There should have been an existing partition table including your Windows partition.  Creating a new partition table would have scrapped the Windows partition.  And while a swap partition isn't strictly necessary, you won't be able to put your computer into hibernation mode without one.

---

### Post by unleashed26 on 2009-01-25
Yikes. I really should have taken more care. Thanks for your help, anyway.

---

