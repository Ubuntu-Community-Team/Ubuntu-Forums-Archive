---
title: "Problem mounting FakeRAID"
date: 2008-12-28
forum: General Help
---

### Post by rosivrepus on 2008-12-28
I made a fresh Ubuntu 8.10 install on a single 250 GB disk, but I am unable to mount my additional fakeraid drives. The RAID contains one NTFS formatted partition and I have been using it in Windows.

Now that I replaced Windows with Ubuntu I still would like to be able to use the data on the RAID.

I am a newby to Linux and tried everything I found on Google, but could not make it work. Please help...

The disks are activated using dmraid:
```
sudo dmraid -ay
ERROR: sil: only 3/4 metadata areas found on /dev/sdc, electing...
/dev/sdc: "sil" and "jmicron" formats discovered (using jmicron)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "jmicron" formats discovered (using jmicron)!
RAID set "jmicron_Gigabyte RAID" already active

```

The drives seems to be okay:
```
sudo dmraid -r
ERROR: sil: only 3/4 metadata areas found on /dev/sdc, electing...
/dev/sdc: "sil" and "jmicron" formats discovered (using jmicron)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "jmicron" formats discovered (using jmicron)!
/dev/sdc: jmicron, "jmicron_Gigabyte RAID", stripe, ok, 625142272 sectors, data@ 0
/dev/sdb: jmicron, "jmicron_Gigabyte RAID", stripe, ok, 625142272 sectors, data@ 0

```

jmicron_Gigabyte RAID shows up in mapper:
```
 ls -la
total 0
drwxr-xr-x  2 root root      80 2008-12-29 00:56 .
drwxr-xr-x 15 root root   14700 2008-12-29 01:20 ..
crw-rw----  1 root root  10, 59 2008-12-29 00:56 control
brw-rw----  1 root disk 254,  0 2008-12-29 00:56 jmicron_Gigabyte RAID

```

but I am unable to mount:
```
sudo mount /dev/mapper/jmicron_Gigabyte\ RAID /media/NTFSRaid -t ntfs-3g
NTFS signature is missing.
Failed to mount '/dev/mapper/jmicron_Gigabyte RAID': Invalid argument
The device '/dev/mapper/jmicron_Gigabyte RAID' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I cannot perform fdisk on the RAID, so I don't know what the partition is called:
```
/dev/mapper$ sudo fdisk jmicron_Gigabyt\ RAID

Unable to open jmicron_Gigabyt RAID

```

Normal fdisk returns:
```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d7a13bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x305d09da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77827   625139712    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1012 MB, 1012924416 bytes
2 heads, 63 sectors/track, 15701 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x04b79d98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15702      989168    6  FAT16

```

Please help.

---

### Post by rosivrepus on 2008-12-29
My motherboard is a Gigabyte P35C-DS3R.

---

### Post by Mathboy on 2008-12-29
Looks similar to this:

[http://ubuntuforums.org/archive/index.php/t-678745.html](http://ubuntuforums.org/archive/index.php/t-678745.html)

What does

sudo fdisk /dev/mapper/jmicron_Gigabyte\ RAID

give you?

---

### Post by rosivrepus on 2008-12-29
thank you for your reply.

This is what happens:
```
sudo fdisk /dev/mapper/jmicron_Gigabyte\ RAID 

The number of cylinders for this disk is set to 77826.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

```

command p:
```
Command (m for help): p

Disk /dev/mapper/jmicron_Gigabyte RAID: 640.1 GB, 640145686528 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x305d09da

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/jmicron_Gigabyte RAID1   *           1       77827   625139712    7  HPFS/NTFS

```

unfortunately mounting does not work
```
sudo mount /dev/mapper/jmicron_Gigabyte\ RAID1 /media/NTFSRaid -t ntfs-3g
ntfs-3g: Failed to access volume '/dev/mapper/jmicron_Gigabyte RAID1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
```

---

### Post by fjgaude on 2008-12-29
> sudo mount /dev/mapper/jmicron_Gigabyte\ RAID1 /media/NTFSRaid -t ntfs-3g

Try mounting without the "\", backslash. Where did that come from?

And leave out the "-3g" from the ntfs.

You did create the mountpoint at /media/NTFSRaid?

---

### Post by rosivrepus on 2008-12-29
/media/NTFSRaid exists, that is not the problem.

without the \ does not work either:
```
sudo mount /dev/mapper/jmicron_Gigabyte RAID /media/NTFSRaid -t ntfs
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
...

```

I tried both suggestions, but still the same errors.

```
sudo mount /dev/mapper/"jmicron_Gigabyte RAID" /media/NTFSRaid
mount: you must specify the filesystem type

```

```
sudo mount /dev/mapper/jmicron_Gigabyte\ RAID /media/NTFSRaid -t ntfs
NTFS signature is missing.
Failed to mount '/dev/mapper/jmicron_Gigabyte RAID': Invalid argument
The device '/dev/mapper/jmicron_Gigabyte RAID' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

Meanwhile I also tried Fedora Core 10, it yields a little different result:
```
dmraid -ay
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "jmicron" formats discovered (using jmicron)!
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
/dev/sda: "sil" and "jmicron" formats discovered (using jmicron)!
RAID set "jmicron_Gigabyte RAID" already active
RAID set "jmicron_Gigabyte RAIDp1" was not activated
```
But I am not able to mount both of them. Is there some way to activate the jmicron_Gigabyte RAIDp1?

I feel like I read almost any page on the internet about mounting FakeRaids, but I did not find the solution.

---

### Post by fjgaude on 2008-12-29
I can't, the think that is strange is the space between the **Gigabyte** and **RAID**... doesn't make since.

You might try an underscore, "_", instead of the \ or space.

I'm sure it is any **dmraid** issue, not knowing what to do in this situation.

---

### Post by rosivrepus on 2008-12-30
The space is just part of the name, but I cannot change it in de RAID BIOS.

Using any other character results in failure:
```
sudo mount /dev/mapper/jmicron_Gigabyte_RAID /media/NTFSRaid -t ntfs
ntfs-3g: Failed to access volume '/dev/mapper/jmicron_Gigabyte_RAID': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
```

---

### Post by rosivrepus on 2008-12-30
I found a solutions.

When running the Fedora Core 10 live CD, I selected manual partitioning during the installation. Then I noticed that my "/dev/mapper/jmicron_Gigabyte\ RAIDp1" was listed.

Suddenly I was able to mount "/dev/mapper/jmicron_Gigabyte RAIDp1" without any problems as a NTFS partition.

Next I had to mount my hard disk with the already installed OS. But I encrypted it. This is my solution for that problem (must be executed as root user):

First prepare kernel
```
modprobe dm-crypt
```

Load partition in cryptsetup (sdc2 is my partition, you can find out the name of yours via fdisk -l)
```
cryptsetup luksOpen /dev/sdc2/ crypt1
```
Enter the passphrase.

Next activate the partitions
```
vgscan --mknodes
vgchange -ay
```

Now the partition shows up in /dev/mapper/ and I was able to mount it.

Finally, I was able to copy the data from my FakeRAID array to my Encrypted LVM partition.

Once I migrated all the data I will create a Linux software RAID.

---

