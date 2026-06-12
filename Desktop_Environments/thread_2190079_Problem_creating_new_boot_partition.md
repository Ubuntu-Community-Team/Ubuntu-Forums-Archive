---
title: "Problem creating new boot partition"
date: 2013-11-25
forum: Desktop Environments
---

### Post by eric.vlaanderen on 2013-11-25
I have recently had a hard drive failure (on an ssd of all things), the hard drive contained my boot partition for both windows and ubuntu - (however i still see both options at startup).

To fix the problem I tried to follow the instructions here:
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

I did the repair twice as the first time i accidently installed the boot on sda1 (ubuntu installation) instead of sda2 (the boot partitiion) (skipping Step 6 of the instructions on the above link)

On startup i still see both of the boot options (windows and ubuntu), neither of which work.

BootInfo Summary:
[http://paste.ubuntu.com/6475531/](http://paste.ubuntu.com/6475531/)

I think the problem may be the first BootRepair, however i'm not sure how to fix it if another boot repair doesn't fix it.

Thanks for the help,
Eric

---

### Post by oldfred on 2013-11-25
You are only showing one drive with two MBR based Linux partitions. That will only boot in BIOS mode.

Boot-Repair says you booted it in UEFI mode with secure boot on. BIOS & UEFI are not really compatible. You have to set one or the other in UEFI/BIOS and use that.
Windows only boots from gpt drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) drives with BIOS mode.
And Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS if correct supporting partitions are on drive.

An efi partition which has boot files is not a /boot partition (normally).

---

### Post by eric.vlaanderen on 2013-11-26
Hi, Thanks for the help - you are correct, my laptop is set up for UEFI boot.

I followed instructions here:
[https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition](https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition)

However I still get the same issue - (same boot options, still nothing when i try to use them)

I'm tempted by the "Reset to setup mode" option in BIOS, however thought i would post here before attempting to play with the BIOS too much.

My BootInfo Summary:
[http://paste.ubuntu.com/6476447/](http://paste.ubuntu.com/6476447/)

Thanks in advance,
Eric

---

### Post by fantab on 2013-11-26
> parted -l:

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End    Size   Type     File system  Flags
2      2097kB  212MB  210MB  primary  fat32        boot
1      212MB   256GB  256GB  primary  ext4


The 'parted -l' output shows that you have 'msdos' partition table. Now this is not compatible with UEFI/EFI boot. Neither Windows or Ubuntu will boot from 'msdos' disk in EFI mode. The FAT32 EFI partition is useless here.

Your options:
1. If you want to boot in EFI mode you need a GUID Partition Table [GPT]. So you will convert/reformat your SSD as GPT disk. [Recommended]
Or.
2. Disable UEFI/EFI boot in BIOS and Enable 'Legacy/CSM Boot'. 

Pick your bet and will guide your further.

---

### Post by oldfred on 2013-11-26
I would not expect the one key or UEFI/BIOS vendor recovery to work either. That depends on the data in the recovery partition which also is now missing from drive.

If you have a backup of recovery or Windows you can probably restore those but may have to delete the Linux partitions first. Windows does not see Llnux correctly, but often sees that there is a partition and does not overwrite it.

---

