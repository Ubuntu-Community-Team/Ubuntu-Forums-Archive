---
title: "zeroing MBR did not eliminate partitions !?"
date: 2009-02-21
forum: General Help
---

### Post by rnsc on 2009-02-21
I always zero the MBR (Actually a few hundred MB) of a disk before I re-purpose it.  On rare but frustrating occasions something in the past use will mess me up.  This gives me a pristine start.

I zeroed them, and the partitions are still there, even after a reboot, and I have verified that the MBRs are zero'ed!  Can somebody help me to understand what is going on?  

Below is the detail of what I did, exactly:

ubuntu 08.10, fairly clean install.  Added a few packages (samba, lvm, mdadm) and did updates last night.

gparted HUNG (No ping, no nothing, had to reset) when scanning the disks.  Previous use of disks was OpenSolaris 2008.11, so I figured whatever Solaris put on the disks confused it.  Fine.  I will zero them:

I did the following to zero out a disk (actually 6):

for i in b c d e f g
do
dd if=/dev/zero of=/dev/sd$i bs=65536 count=8192
done

partprobe
cat /proc/partitions

Partitions were still there!  Well, partprobe is new to me...maybe it does not work, or I don't understand it.

Reboot.

cat /proc/paritions

Partitions still there!

dd if=/dev/sdc bs=512 count=1 | od

All zeros!

cat /proc/partitions
All partitions there!

I have never heard of a backup / alternate / second copy of the DOS partition table.  Searching on the Internet does not turn up any such thing.

Any idea what is happening?

---

### Post by caljohnsmith on 2009-02-21
How about first posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by rnsc on 2009-02-21
Thank you, you triggered what I needed to get un-stuck.  

I am used to using /proc/partitions when doing Linux and Windows work, but that shows all of the the partitions recognized by the kernel.  fdisk shows only the partitions in the DOS partition table chain.  

"fdisk -lu" shows no partitions (appended below).  

The system (and disks) had been used last with Solaris.  Solaris slices had been defined, and the kernel was finding them and making them accessible as /dev/sd*, as documented in /proc/partitions.  (See slice of messages file below the fdisk output.  Notice the word "Solaris" and the mapping from slice to sd*).

Evidently the Solaris VTOC is not kept in the first few hundred MB of the disk.  Probably in the last cylinder; this rings a vague bell.  Clearly this is out of scope of this forum.

What is interesting is that the Solaris slices were created within a DOS partition.  So without the DOS partition table, how did the Linux kernel know where to find the slices?  I suspect that since it did not find a valid DOS partition table, it checked for a Solaris VTOC wherever it was supposed to be and found it (presumably the end of the disk).  This would be how Solaris SPARC disks were.  Since the DOS partition containing the Solaris slices abutted the end of the disk, the VTOC was where it would have been for a SPARC Solaris disk!  *Before* I zero'ed the MBR, it would have found the right partition, gone to the end of it, and found the VTOC!  This is all conjecture unless/until I can find a document presenting the Solaris disk layout, but so far I have not been able to.

I am (and will be for the next ten hours) writing zeros into EVERY sector of the disks.  Guess I will setup LVM tomorrow.

Thanks again.

---------
fdisk -lu
---------
Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders, total 60074784 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d02da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      257039      128488+  83  Linux
/dev/sda2          257040    60067034    29904997+   5  Extended
/dev/sda5          257103    28161944    13952421   83  Linux
/dev/sda6        28162008    32162129     2000061   82  Linux swap / Solaris
/dev/sda7        32162193    60067034    13952421   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table

-------------------------------------------------
HOWEVER looking at /var/log/messages during boot:
-------------------------------------------------

Feb 21 11:43:21 rnscserver kernel: [   10.100465] Driver 'sd' needs updating - please use bus_type methods
Feb 21 11:43:21 rnscserver kernel: [   10.100824] sd 0:0:0:0: [sda] 60074784 512-byte hardware sectors (30758 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.100879] sd 0:0:0:0: [sda] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.100977] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.101176] sd 0:0:0:0: [sda] 60074784 512-byte hardware sectors (30758 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.101225] sd 0:0:0:0: [sda] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.101320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.101335]  sda: sda1 sda2 < sda5<4>Driver 'sr' needs updating - please use bus_type methods
Feb 21 11:43:21 rnscserver kernel: [   10.148659]  sda6 sda7 >
Feb 21 11:43:21 rnscserver kernel: [   10.164786] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.165474] sd 1:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.165571] sd 1:0:0:0: [sdb] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.165673] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.165877] sd 1:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.165929] sd 1:0:0:0: [sdb] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.166028] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.166041]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Feb 21 11:43:21 rnscserver kernel: [   10.171307] Uniform CD-ROM driver Revision: 3.20
Feb 21 11:43:21 rnscserver kernel: [   10.173442]  sdb1
Feb 21 11:43:21 rnscserver kernel: [   10.179310]  sdb1: <solaris: [s2] sdb5 [s4] sdb6 [s5] sdb7 [s8] sdb8 [s9] sdb9 >
Feb 21 11:43:21 rnscserver kernel: [   10.179983] sd 1:0:0:0: [sdb] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.180376] sd 1:0:1:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.180435] sd 1:0:1:0: [sdc] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.180538] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.180732] sd 1:0:1:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.180784] sd 1:0:1:0: [sdc] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.180884] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.180898]  sdc: sdc1
Feb 21 11:43:21 rnscserver kernel: [   10.193566]  sdc1: <solaris: [s2] sdc5 [s4] sdc6 [s5] sdc7 [s8] sdc8 [s9] sdc9 >
Feb 21 11:43:21 rnscserver kernel: [   10.194239] sd 1:0:1:0: [sdc] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.194524] sd 2:0:0:0: [sdd] 390721968 512-byte hardware sectors (200050 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.194579] sd 2:0:0:0: [sdd] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.194676] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.194868] sd 2:0:0:0: [sdd] 390721968 512-byte hardware sectors (200050 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.194916] sd 2:0:0:0: [sdd] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.195010] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.195024]  sdd: sdd1
Feb 21 11:43:21 rnscserver kernel: [   10.222584]  sdd1: <solaris: [s2] sdd5 [s4] sdd6 [s5] sdd7 [s8] sdd8 [s9] sdd9 >
Feb 21 11:43:21 rnscserver kernel: [   10.223309] sd 2:0:0:0: [sdd] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.223597] sd 2:0:1:0: [sde] 390721968 512-byte hardware sectors (200050 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.223655] sd 2:0:1:0: [sde] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.223762] sd 2:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.223955] sd 2:0:1:0: [sde] 390721968 512-byte hardware sectors (200050 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.224004] sd 2:0:1:0: [sde] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.224148] sd 2:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.224162]  sde: sde1
Feb 21 11:43:21 rnscserver kernel: [   10.250484]  sde1: <solaris: [s2] sde5 [s4] sde6 [s5] sde7 [s8] sde8 [s9] sde9 >
Feb 21 11:43:21 rnscserver kernel: [   10.251191] sd 2:0:1:0: [sde] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.251469] sd 3:0:0:0: [sdf] 234441648 512-byte hardware sectors (120034 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.251528] sd 3:0:0:0: [sdf] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.251633] sd 3:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.251845] sd 3:0:0:0: [sdf] 234441648 512-byte hardware sectors (120034 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.251898] sd 3:0:0:0: [sdf] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.252000] sd 3:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.252068]  sdf: sdf1
Feb 21 11:43:21 rnscserver kernel: [   10.278512]  sdf1: <solaris: [s2] sdf5 [s4] sdf6 [s8] sdf7 [s9] sdf8 >
Feb 21 11:43:21 rnscserver kernel: [   10.280267] sd 3:0:0:0: [sdf] Attached SCSI disk
Feb 21 11:43:21 rnscserver kernel: [   10.280589] sd 3:0:1:0: [sdg] 234441648 512-byte hardware sectors (120034 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.280646] sd 3:0:1:0: [sdg] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.280749] sd 3:0:1:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.280975] sd 3:0:1:0: [sdg] 234441648 512-byte hardware sectors (120034 MB)
Feb 21 11:43:21 rnscserver kernel: [   10.281026] sd 3:0:1:0: [sdg] Write Protect is off
Feb 21 11:43:21 rnscserver kernel: [   10.281126] sd 3:0:1:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 21 11:43:21 rnscserver kernel: [   10.281139]  sdg: sdg1
Feb 21 11:43:21 rnscserver kernel: [   10.301458]  sdg1: <solaris: [s2] sdg5 [s4] sdg6 [s8] sdg7 [s9] sdg8 >
Feb 21 11:43:21 rnscserver kernel: [   10.302147] sd 3:0:1:0: [sdg] Attached SCSI disk

---

