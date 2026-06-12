---
title: "Auto Fsck Checks Partitions not in fstab and Corrupts Data"
date: 2009-01-05
forum: General Help
---

### Post by init1 on 2009-01-05
When I booted into FreeDOS today, I noticed that there were a lot of small files starting with "fsck00" in the root of the partition, and I'm missing a lot of files. This is right after Ubuntu did a auto fsck, so I assume that's what caused it. My DOS partition is not in my fstab though, so why is it being checked?! I'm worried that fsck may have corrupted the filesystem, since I'm missing quite a few files.

---

### Post by hansdown on 2009-01-05
Hi init1.

There is a bug report.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/48806](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/48806)

It's from a couple years ago though.

---

### Post by init1 on 2009-01-06
> **hansdown said:**
> Hi init1.

There is a bug report.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/48806](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/48806)

It's from a couple years ago though.
Thanks, looks like there's nothing I can do though. I've lost a lot of respect for Ubuntu after this though. How could such a severe bug be ignored for so long?

---

### Post by mcduck on 2009-01-06
Add the partitions to fstab (with "noauto"-option if you don't want to mount them) and make sure the last number in their entry lines is "0".

Sounds funny that fsck would check prtitions not mentioned in fstab, but this way you can at least specifically tell it to _not_ check that drive.

You could also post your fstab and outputs of "sudo fdisk -l" and "blkid" here. That way we'd have a lot more to work with.

---

### Post by init1 on 2009-01-06
OK, he's what I have:
fdisk
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d73e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           30341       30401      489982+  82  Linux swap / Solaris
/dev/sda2               1       30158   242244103+  83  Linux
/dev/sda3   *       30159       30340     1461915    b  W95 FAT32

```

blkid
```

/dev/sda1: UUID="08401b78-3ac9-4cf3-a383-78406c3843ba" TYPE="swap" 
/dev/sda2: UUID="7aa7d23b-7a37-4cae-80dc-13954a18ed68" TYPE="ext3" 
/dev/sda3: UUID="98B8-DBF4" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

```

fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7aa7d23b-7a37-4cae-80dc-13954a18ed68 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=08401b78-3ac9-4cf3-a383-78406c3843ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Yeah, I guess I could add it to fstab just so that it wouldn't get checked. I'll look up syntax later.

---

### Post by dcstar on 2009-01-06
> **init1 said:**
> When I booted into FreeDOS today, I noticed that there were a lot of small files starting with "**fsck00**" in the root of the partition, and I'm missing a lot of files. This is right after Ubuntu did a auto fsck, so I assume that's what caused it.
.......


And what is the date stamp on those files?

---

