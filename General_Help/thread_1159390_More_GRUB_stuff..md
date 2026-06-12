---
title: "More GRUB stuff."
date: 2009-05-14
forum: General Help
---

### Post by PupSpark on 2009-05-14
I have 2 hard drives, one internal with Ubuntu 8.10, one external with Ubuntu 9.04, and a BIOS that doesn't support USB. The one on the internal hard drive has KGRUBEditor and Firefox on it. The one on the external is my main hard drive. Since my BIOS doesn't support USB, I want to somehow boot from the internal HD's GRUB menu, by either setting it to boot the kernel directly or to use a chainloader. 

When I use a chainloader, it gives me error 13, and when I set it to boot from the kernel, it gives me error 18.

13 : "Inconsistent filesystem structure" (Although it gives me something about my BIOS cylinder not being able to handle it or something)
18 : "Invalid or unsupported executable format"

Thanks!

---

### Post by mikewhatever on 2009-05-14
You should post the outputs of the following, otherwise it would be just guess work:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by PupSpark on 2009-05-15
I'm not sure what you mean, so I'll upload menu.lst and device.map to see if that gives you any insight. Attachment.

---

### Post by mikewhatever on 2009-05-15
You should still post the output of **sudo fdisk -l** to verify the partitions are correct. Can you boot 8.10 from the internal HDD?

---

### Post by PupSpark on 2009-05-15
> **mikewhatever said:**
> You should still post the output of **sudo fdisk -l** to verify the partitions are correct. Can you boot 8.10 from the internal HDD?

The 8.10 that is on the internal HDD? Yes.

Here's the result of sudo fdisk -l:

On my internal hard drive:
>  
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37439451   83  Linux
/dev/sda2            4662        4866     1646662+   5  Extended
/dev/sda5            4662        4866     1646631   82  Linux swap / Solaris


This is the computer that my HDD is currently plugged into, which is why it lists sda, which windows is installed on. (irrelevant)
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fb05f41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f754

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30025   241175781   83  Linux
/dev/sdb2           30026       30401     3020220    5  Extended
/dev/sdb5           30026       30401     3020188+  82  Linux swap / Solaris


---

### Post by mikewhatever on 2009-05-16
I see you are trying to use root (hd1.0) for Jaunty in menu.lst, which is supposed to be sdb1, yet there is no mention of sdb in the device.map, and hd1 is recognised as sdc. Have you tried removing the root (hd1,0) line?

---

### Post by PupSpark on 2009-05-16
> **mikewhatever said:**
> I see you are trying to use root (hd1.0) for Jaunty in menu.lst, which is supposed to be sdb1, yet there is no mention of sdb in the device.map, and hd1 is recognised as sdc. Have you tried removing the root (hd1,0) line?
I don't know. It skipped sdb... 

But isn't my external hard drive (hd1,0)?

---

### Post by mikewhatever on 2009-05-16
There is a line, root (hd1,0), try removing it. According to fstab, your external drive is /dev/sdb, but according to device.map, /dev/sdc = hd1, and /dev/sdb isn't even there.

---

### Post by PupSpark on 2009-05-16
Wouldn't it say disk not found or something? (In the first place, I mean)

I'm trying it anyway...

EDIT: still says the selected cylinder exceeds the capacity of BIOS. I'm going to try completely removing the "Root" line.

That just says file not found. The chainloader still says error 13. 

But look at this; this is from 8.04 and 9.10 on the same computer:
> Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37439451   83  Linux
/dev/sda2            4662        4866     1646662+   5  Extended
/dev/sda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f754

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30025   241175781   83  Linux
/dev/sdc2           30026       30401     3020220    5  Extended
/dev/sdc5           30026       30401     3020188+  82  Linux swap / Solaris


It's sdc on this computer!

---

### Post by PupSpark on 2010-02-14
Hate to bump huge, but I found a solution to this problem.

I copied my entire boot folder (including the kernel) from the original external drive (partition A) to the root of a new partition (I'll call it partition B) on my external hard drive. Then I installed grub on the other partition, partition C(I did this by installing ubuntu). I copied the info of certain files (I'm sorry about not knowing this, this was months ago; I'll take a look later to refresh my memory EDIT: They were menu.lst and device.map) that had the UUID of the kernel on partition B onto the same files on partition C. The kernel on Partition B used the files from Partition A to run, so it was almost as if booting from USB!

Unfortunately, this was way too much for the HD hard drive to handle, especially since I partitioned it so many times, so, after a few mothns, I had to stop running from it so it didn't break. So I only reccommend this if you have time to waste and an external hard drive you don't need.

Thanks for all your help, and sorry for the dredge!

---

