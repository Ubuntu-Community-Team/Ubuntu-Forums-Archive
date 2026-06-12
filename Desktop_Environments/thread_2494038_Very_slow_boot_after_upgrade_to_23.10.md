---
title: "Very slow boot after upgrade to 23.10"
date: 2024-01-03
forum: Desktop Environments
---

### Post by wsanborn on 2024-01-03
My desktop is a Dell OptiPlex 990 with an Intel i7-2600x8 processor, graphics Nvidia Geforce GT 1030 using Nvidia Driver 535.129.03. I'm obviously not a gamer.

After I upgraded to 23.10 (from 23.04) the time between Grub and Login increased to a very annoying 3-4 minutes. After many google searches finding no obvious solutions, I zeroed in on the problem using the boot output by using Grub Optimizer (Advanced settings) to deactivate "quiet splash". This allowed me to observe the timeout events that were causing the delays.

Detail from /var/log/boot.log report:

[    2.595885] sd 7:0:0:0: [sdf] Media removed, stopped polling
[    2.596435] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[   32.188074] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   32.190814] ata2.00: configured for UDMA/100
[   62.907952] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   62.910519] ata2.00: configured for UDMA/100
[   93.644022] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   93.646624] ata2.00: configured for UDMA/100
[  124.037382] ata2.00: limiting speed to UDMA/66:PIO4
[  124.352040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  129.377372] ata2.00: qc timeout after 5000 msecs (cmd 0xa1)
[  129.379579] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  129.379647] ata2.00: revalidation failed (errno=-5)
[  129.695968] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  139.873356] ata2.00: qc timeout after 10000 msecs (cmd 0xa1)
[  139.875561] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  139.875635] ata2.00: revalidation failed (errno=-5)
[  140.191998] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  150.971012] EXT4-fs (sda9): mounted filesystem 088c2c8f-06a5-4017-8144-41eb1fddb6ad ro with ordered data mode. Quota mode: none.
[  171.105365] ata2.00: qc timeout after 30000 msecs (cmd 0xa1)
[  171.107572] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  171.107645] ata2.00: revalidation failed (errno=-5)
[  171.107714] ata2.00: disable device
[  171.423988] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  171.425540] sr 1:0:0:0: [sr0] scsi-1 drive
[  171.425617] cdrom: Uniform CD-ROM driver Revision: 3.20
[  171.426250] sr 1:0:0:0: Attached scsi CD-ROM sr0

Turns out that there is some sort of Sata link problem that was introduced with 23.10 and the original OptiPlex 990 CD/DVD unit (a TSST TS-H653H). Disconnecting or replacing the unit solves the problem (boots in under 10 seconds). Not sure if this is a bug in the new kernel or a problem with the drive. Hope this helps someone.

---

