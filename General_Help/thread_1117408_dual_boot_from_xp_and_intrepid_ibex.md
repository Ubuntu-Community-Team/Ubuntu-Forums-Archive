---
title: "dual boot from xp and intrepid ibex"
date: 2009-04-05
forum: General Help
---

### Post by sicksix on 2009-04-05
I am having issues with dual booting windows XP and ubuntu intrepid ibex..   windows XP is on my C drive and when I installed ubuntu on E drive, E is no longer shown in windows xp based upon, I guess the format type of the drive..  Anyway, I used easyBCD to try and get the boot loader going but it is showing that unbuntu is on C drive instead of E drive..  I see there is a file on the C drive that has /NST/grub/menu.lst file on my C drive but I guess that needs to be on the E drive right?!?  Please assist me with getting this taken care of so I can boot both my Windows XP on C and Ubuntu on E drive...  Here is a list of my drives,

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x13d09d06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41344   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1c70416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       29638   238067203+  83  Linux
/dev/sdc2           29639       30394     6072570    5  Extended
/dev/sdc5           29639       30394     6072538+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16f4e251

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 127 MB, 127926272 bytes
16 heads, 32 sectors/track, 488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         488      124911+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(486, 15, 32) logical=(487, 15, 31)

Any help would be greatly appreciated!! I have no idea what I am doing.. :)

---

### Post by wolfen69 on 2009-04-05
sounds like grub is messed up. see [this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Bakon Jarser on 2009-04-05
It looks like your e drive is too small for ubuntu.  A 127 Mb drive is not really worth keeping in your system when all of your other drives dwarf it in storage capacity.  In my opinion it is a waste of electricity.  It looks like linux is installed on your c drive.  If windows was on that drive before I think you may have overwritten it.  Do both windows and ubuntu currently boot?  If not can you post your menu.lst file here?

---

### Post by sicksix on 2009-04-05
> **Bakon Jarser said:**
> It looks like your e drive is too small for ubuntu.  A 127 Mb drive is not really worth keeping in your system when all of your other drives dwarf it in storage capacity.  In my opinion it is a waste of electricity.  It looks like linux is installed on your c drive.  If windows was on that drive before I think you may have overwritten it.  Do both windows and ubuntu currently boot?  If not can you post your menu.lst file here?

the 127 drive is my flash drive.. i just forgot to remove it.. ;)

---

### Post by Bakon Jarser on 2009-04-06
Okay, so I guess you meant C: and E: in your original post, which is not the same as sdc and sde.  Do you have both windows and ubuntu booting now?

---

### Post by sicksix on 2009-04-06
> **wolfen69 said:**
> sounds like grub is messed up. see [this]("http://ubuntuforums.org/showthread.php?t=224351").

I did the grep deal..... When I went back to EasyBCD 1.7.2 in windows xp, it still shows this, 

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 5 seconds.
Default OS: Windows XP

Entry #1

Name:  Windows XP
BCD ID:  {default}
Drive:  C:\
Bootloader Path:  \NTLDR

Entry #2

Name:  Ubuntu
BCD ID:  {1ed367a0-14f6-11de-ac3c-0018f80d8f88}
Drive:  C:\
Bootloader Path:  \NST\nst_grub.mbr

Ubuntu should be going to E:\ 
What gives there?  Do I need to use the GRUB boot screen instead of my Windows boot screen?  I dont know where to go with this..

---

