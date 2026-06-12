---
title: "NTFS file system help!"
date: 2009-01-07
forum: General Help
---

### Post by kneewax on 2009-01-07
I have a problem on the one non-linux machine in the house.

My wife's PC has XP Pro installed and two SATA HDDs.  The second of these has been corrupted by a recent power outage and XP cannot see the disk at all.

AHA I though, I'll mount it using my Ubuntu Live CD and try to rescue it that way.  However although Ubuntu can see the disk it won't mount.  I don't know enough about Ubuntu and NTFS to get mysefl out of this hole.  I tried a forced mount, but couldn't get anywhere.

Anyone got any ideas - the data on the disk is quite valuable to us and I really want to restore it long wnough to copy everything off....

Thanks

---

### Post by caljohnsmith on 2009-01-07
With the HDD in question connected, how about posting:
```
sudo fdisk -lu
```
Also, what error do you get when you force mount it?

---

### Post by kneewax on 2009-01-09
Sorry I haven't replied before, things got busy and I haven't had a chance to boot this machine with the live disk so I could do this.

fdisk -lu posted this:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12678     4209029     2098176   27  Unknown
/dev/sda2   *     4225095   132841484    64308195    7  HPFS/NTFS
/dev/sda3       132841485   488392064   177775290    7  HPFS/NTFS

Disk /dev/sdc: 19 MB, 19922944 bytes
10 heads, 41 sectors/track, 94 cylinders, total 38912 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           7       38911       19452+   4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(38, 9, 41) logical=(94, 9, 3)

Disk /dev/sdd: 3999 MB, 3999793152 bytes
98 heads, 33 sectors/track, 2415 cylinders, total 7812096 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            8192     7812095     3901952    b  W95 FAT32

```

when I try to force the mount I get the following error:

```

Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

any help appreciated.  Thanks

---

### Post by caljohnsmith on 2009-01-09
So when you said that your wife's XP Pro was installed on two HDDs, what do you mean? Were they in a RAID configuration? Also, is the 250 GB drive that fdisk showed the drive in question? If so, I would boot your Windows Install CD, go to the "recovery console", and do:
```
map
```
That will give the drive letters of all the NTFS partitions on the drive, so then you can do:
```
chkdsk /r C:
```
And replace C with the drive letters of each of the NTFS partitions. I would run chkdsk on each NTFS partition as many times as it takes until it reports no errors. After that, try mounting the partition again in Ubuntu, and let me know if you still get the same error. We can work from there.

---

### Post by wolfen69 on 2009-01-09
you could also try the puppy linux live cd to recover the files. puppy is a very powerful little distro.

---

