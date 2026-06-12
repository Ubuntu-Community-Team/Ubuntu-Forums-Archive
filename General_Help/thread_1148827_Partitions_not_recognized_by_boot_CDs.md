---
title: "Partitions not recognized by boot CDs"
date: 2009-05-04
forum: General Help
---

### Post by Sadistic Tribble on 2009-05-04
A few weeks ago, I installed Kubuntu 8.10 on my laptop, and everything seemed to be working. When installing Kubuntu, I split the drive into three partitions: One for Kubuntu, one for swap, and one for windoze later. I then installed windoze onto the other partition, and it no longer reads from the Grub loader (naturally).

That's fine, I want to install Kubuntu 9.04 anyway.
But nothing- the Kubuntu installer, the GPartEd or the Partition Logic boot CDs- will recognize my partitions. It just sees 80GB (my HDD) of unpartitioned space. 

[Swissknife]("http://www.compuapps.com/download/Swissknife/swissknife.htm") can be run while windoze is running (not as a bootCD), but it can't /edit/ any partitions. It sees all the partitions fine. When I run it, I see the 30GB windoze partition as primary and the partitions for Kubuntu (data and swap).

So... why can't any boot CDs see the partitions?

---

### Post by caljohnsmith on 2009-05-04
It sounds like your HDD probably has a corrupt partition table, because that can often happen when using a Windows partition program on a drive that has linux partitions. To see if that's your case, how about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
And we can work from there if you want. 

Regards,
John

---

### Post by bigcat42 on 2009-05-04
I'm having a similar problem. GParted reads my entire hard drive as "unallocated", but Windows recognizes the partitions without any trouble. It's a Dell laptop with dual boot Vista & Ubuntu (plus Dell's usual hidden partitions).

This is the result of the commands you mentioned.

```
~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   229804032   234438655     2317312    c  W95 FAT32 (LBA)
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3   *    21133312   138573823    58720256    7  HPFS/NTFS
/dev/sda4       138576751   234438655    47930952+   f  W95 Ext'd (LBA)
/dev/sda5       229804032   234438655     2317312   dd  Unknown
/dev/sda6   *   138576753   225970289    43696768+  83  Linux
/dev/sda7       225970353   229793759     1911703+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

```
sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=229804032, size=  4634624, Id= c, bootable
/dev/sda2 : start=   161792, size= 20971520, Id= 7
/dev/sda3 : start= 21133312, size=117440512, Id= 7, bootable
/dev/sda4 : start=138576751, size= 95861905, Id= f
/dev/sda5 : start=229804032, size=  4634624, Id=dd
/dev/sda6 : start=138576753, size= 87393537, Id=83, bootable
/dev/sda7 : start=225970353, size=  3823407, Id=82
```

```
~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```

---

### Post by caljohnsmith on 2009-05-04
> **bigcat42 said:**
> 
```
~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   [COLOR="Red"]229804032   234438655[/COLOR]     2317312    c  W95 FAT32 (LBA)
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3   *    21133312   138573823    58720256    7  HPFS/NTFS
/dev/sda4       138576751   234438655    47930952+   f  W95 Ext'd (LBA)
/dev/sda5       [COLOR="Red"]229804032   234438655[/COLOR]     2317312   dd  Unknown
/dev/sda6   *   138576753   225970289    43696768+  83  Linux
/dev/sda7       225970353   229793759     1911703+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

It looks like the reason your HDD shows up as unallocated in gparted is because your HDD's partition table is unfortunately corrupt. As shown highlighted in red above, your sda1 primary partition is a duplicate of the sda5 logical partition. My recommendation would be to delete the sda1 partition and keep the sda5 partition, because those partitions look like they are your Media Direct partition; if they are, the Media Direct partition should be sda5, not sda1. Also, the Media Direct partition should have a file system ID of "dd" like your sda5 partition has, not "c" (FAT32) like your sda1 partition has. So to fix the problem, how about doing:
```
sudo sfdisk -A3 /dev/sda
echo "0,0,0,-" | sudo sfdisk --no-reread -fuS /dev/sda -N1
```
Please post the output of the above commands, reboot, and then post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
If the last parted command shows your partition table without returning any errors, then gparted should be happy too and show all your partitions. Let me know how that goes or if you run into problems.

John

---

### Post by bigcat42 on 2009-05-05
The first command you suggested came back with this confusing response-
```
~$ sudo sfdisk -A1 /dev/sda2
Warning: start=161792 - this looks like a partition rather than
the entire disk. Using fdisk on it is probably meaningless.
[Use the --force option if you really want this]
```

The second appeared to do more-
```
~$ echo "0,0,0,-" | sudo sfdisk --no-reread -fuS /dev/sda -N1
 
Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   * 229804032 234438655    4634624   c  W95 FAT32 (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda2        161792  21133311   20971520   7  HPFS/NTFS
/dev/sda3   *  21133312 138573823  117440512   7  HPFS/NTFS
/dev/sda4     138576751 234438655   95861905   f  W95 Ext'd (LBA)
/dev/sda5     229804032 234438655    4634624  dd  Unknown
/dev/sda6   * 138576753 225970289   87393537  83  Linux
/dev/sda7     225970353 229793759    3823407  82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2        161792  21133311   20971520   7  HPFS/NTFS
/dev/sda3   *  21133312 138573823  117440512   7  HPFS/NTFS
/dev/sda4     138576751 234438655   95861905   f  W95 Ext'd (LBA)
/dev/sda5     229804032 234438655    4634624  dd  Unknown
/dev/sda6   * 138576753 225970289   87393537  83  Linux
/dev/sda7     225970353 229793759    3823407  82  Linux swap / Solaris
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```

After running this, I checked GParted - it works again! Thank you! I originally ran into this problem because I wanted to re-install Ubuntu with ext4... would you expect any further problems to arise? In either event, I'll reboot now & make sure it's all working as expected.

---

### Post by bigcat42 on 2009-05-05
Yes, it all appears to be working! Excellent.

---

### Post by caljohnsmith on 2009-05-05
> **bigcat42 said:**
> Yes, it all appears to be working! Excellent.
That's great news, glad it's all working now. BTW, I corrected that first sfdisk command that you ran that returned the error, so I would suggest running the corrected version again:
```
sudo sfdisk -A3 /dev/sda
```
What that does is set the boot flag on your sda3 partition while removing the boot flag from all your other partitions; only one partition on the HDD should be flagged as bootable, and right now both your sda3 and sda6 partitions have the boot flag set. Therefore I would suggest running the above command so that only sda3 is flagged as bootable. Anyway, cheers and enjoy all your OSes.

John

---

