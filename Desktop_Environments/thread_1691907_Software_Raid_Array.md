---
title: "Software Raid Array???"
date: 2011-02-20
forum: Desktop Environments
---

### Post by phillips321 on 2011-02-20
Hi guys,

Just got 3 extra drives for my machine.
2x160Gb sata
1x 165Gb sata

How do i create a raid0 array of these drives?

On each drive i have got a partition whose size is 160GB and formatted to type fd (Raid Autodetect)

i have tried the following:
```
mdadm --create /dev/md0 --level=0 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sda1
mkfs.ext4 /dev/md0
mount /dev/md0 /media/raid
```

but for some reason it doesnt work.

Also another issue.
the drives do not always have the same device

sometimes the 3 drives are /dev/sdA /dev/sdB and /dev/sdC
... and other times /dev/sdB /dev/sdC and /dev/sdD

any ideas?

Cheers

P.s. is it ok to raid partitions rather than drives?

---

### Post by deconstrained on 2011-02-20
You need to assemble it first before you can use it;
```
# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sda1
```

With regard to the devices not getting the same kernel names on reboots: you should just use the UUID of the array instead of the kernel names (sdb1, sdc1 etc). Pick one of the partitions in the array (i.e. sdb1) and the 'blkid' command command will print information from the superblock, including the UUID (and TYPE="linux_raid_member"). That UUID is common to all the devices in the array and can be used by the kernel and mdadm to assemble the array. Then you can use
```
# mdadm --assemble --uuid=[uuid] /dev/md0
```
To assemble your array at boot time: first assemble the arrays you want to have ready at boot time, then
```
# mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
To be on the safe side, open it with a text editor and make sure that only the arrays you want to assemble are in that file (and remove duplicate entries, if any). Then, rebuild your Linux image:
```
# update-initramfs -k all -c
```

If you're having trouble assembling/mounting, make sure the appropriate module (raid1 in your case) is modprobe'd into the kernel, and fsck.ext4 the volume before mounting (fsck is generally a good idea to do before mounting filesystems). Also, paying close attention to (and sharing) the error messages would help diagnose the problem.

Good luck!

---

### Post by phillips321 on 2011-02-20
```
root@DesktopUbuntu:~# blkid
/dev/sda1: UUID="10e4ff63-3613-43f2-a2d5-049785634c64" TYPE="swap" 
/dev/sda2: UUID="1E223B59223B355D" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="2357075637B4BD39" TYPE="ntfs" 
/dev/sda4: LABEL="Linux" UUID="71fa4d16-5b8d-4e2f-921f-54e09e372905" TYPE="ext4" 
/dev/sdb2: UUID="ca8f0f27-1431-4b75-a16c-cb445fdf0a9e" TYPE="swap" 
/dev/sdd1: UUID="48e267f3-e526-b907-393f-3ca1cbed4451" TYPE="linux_raid_member" 
/dev/sdc1: UUID="48e267f3-e526-b907-393f-3ca1cbed4451" TYPE="linux_raid_member" 
/dev/sde1: LABEL="backup500" UUID="4caffe8f-24e2-48ff-9707-10f1391c934a" TYPE="ext4" 
```


Hmmm, /dev/sdb1 doesn't show up?

```
root@DesktopUbuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdc1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2             125       24439   195310237+   7  HPFS/NTFS
/dev/sda3   *       36620      121601   682617915    7  HPFS/NTFS
/dev/sda4           24440       36619    97835850   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000524fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             567       20023   156288352+  fd  Linux RAID autodetect
/dev/sdb2               1         566     4546363+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031fed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321   fd  Linux RAID autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   fd  Linux RAID autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05a569de

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux

```

---

### Post by deconstrained on 2011-02-20
Explicitly specify which block device to examine; blkid /dev/sdb1.

Just FYI, sometimes the Ubuntu flavor (default configuration) of mdadm can play mind games with you. This is because dpkg adds an initscript and starts mdadm as a service **BY DEFAULT**, and it auto-detects and assembles stuff without you knowing about it or explicitly commanding it, which then results in various block devices being "busy" when they shouldn't be - in short, it thinks it's smart enough to work without your instruction, but in actuality, it's really dumb (and it's pissed me off times aplenty).

Something you could try is stopping mdadm (/etc/init.d/mdadm stop and/or pkill -SIGKILL mdadm), disassembling ALL the arrays (for d in /dev/md*; do mdadm --misc -S $d; done) and then starting over.

---

### Post by phillips321 on 2011-02-21
bklid directed at the device doesnt give any output:
```
root@DesktopUbuntu:~# blkid /dev/sdb1
root@DesktopUbuntu:~# 

```

This is starting to confuse me a great deal now....

---

### Post by deconstrained on 2011-02-21
The reason you cannot see sdb1 may be because mdadm has auto-assembled a half-assed array involving it, so that would make the block device unavailable.

Like I said, it's most likely that mdadm is running as a service and playing mind games with you. KILL IT WITH FIRE, stop all your "md" devices, and then try reassembling. 

Also, if you rebooted since your last attempt, udev may have reassigned device names (i.e. sda,sdb,sdc) in a different order.

---

