---
title: "Sharing a partition"
date: 2009-02-05
forum: General Help
---

### Post by bigbadbrad on 2009-02-05
On my computer I have a NTFS partition with all my music on it. I can get to it fine in ubuntu but not windows. Any ideas on how both OSs can share it?

---

### Post by HermanAB on 2009-02-05
Uhmmm, if it really is NTFS, then Windows MUST be able to access it.  If Windows is screwed up, try using BartPE (bootable Windows CDROM) to fix it.

Cheers,

Herman

---

### Post by bigbadbrad on 2009-02-05
I'm almost positive it's NTFS cause I put the files there using a previous version of Windows. I have Ubuntu and Windows 7 betea on one partition and the music on another.

---

### Post by linuxluver on 2009-02-05
Wait a minute, you used it with a *previous* version of Windows? What do you mean by previous? Windows 98, XP, Vista, what?

---

### Post by trvr on 2009-02-05
Would you mind posting the output of "sudo fdisk -l" (without quotes, and that is a lowercase L), if you are in Ubuntu right now, that is.

Thanks.

---

### Post by bigbadbrad on 2009-02-05
> **linuxluver said:**
> Wait a minute, you used it with a *previous* version of Windows? What do you mean by previous? Windows 98, XP, Vista, what?

Yes, I had Vista installed. Made a partition with the Windows partitioner, copied the music. Installed Ubuntu on the Vista Partition. Today I split the Ubuntu Partition in half and installed the Seven Beta on the half of Ubuntu partition.

I'll get the results of that command in just a sec.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122cd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26108   209712478+   5  Extended
/dev/sda2   *       26109       30402    34477056    7  HPFS/NTFS
/dev/sda5               1         498     4000122   82  Linux swap / Solaris
/dev/sda6             499       13304   102864163+  83  Linux
/dev/sda7           13305       26108   102848098+   7  HPFS/NTFS


---

### Post by trvr on 2009-02-05
Sorry, I'm still a little confused here. What operating systems do you currently have installed? Ubuntu, Vista, and 7? Or did you remove Vista when you installed 7?

---

### Post by bigbadbrad on 2009-02-05
Right now it's Ubuntu and Windows Seven.

---

### Post by nytek on 2009-02-06
Resize one of your partitions and make the extra space another partition. Make sure you make it fat 32, the most stable for shareable data.

---

### Post by mb_webguy on 2009-02-06
Wait.  Have you tried mounting the partition and assigning it a drive letter in Windows Partition Manager?

---

