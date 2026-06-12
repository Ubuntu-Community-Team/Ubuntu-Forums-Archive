---
title: "Mounting an NTFS partition at boot?"
date: 2009-02-18
forum: General Help
---

### Post by Arch_NME on 2009-02-18
I'm trying to get my two NTFS partitions to be automatically mounted by Ubuntu during start up so they are available with out me having to access them from the places menu first. I just want the partitions to be mounted automatically on boot.

Here is the output of **sudo fdisk -l** command

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa693a693

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/sda2            4081       19457   123515752+   7  HPFS/NTFS
/dev/sda3            2041        4080    16386300   83  Linux
```

I edited the **/etc/fstab** file and I added this line.
```
/dev/sda2       /media/local    fuseblk rw,exec,auto,user,sync  0  0
```

I first tried with NTFS in there instead of fuseblk. Neither works I don't really understand why, in fact I can't even mount the Partition at all once I boot with that line in. The drives work fine when ubuntu mounts them normally.

Anyone have any idea what could be going wrong? or can anyone advise me on what command would work?

I'm very new to GNU/Linux so dumb it down for me if possible. Thanks.

---

### Post by Bucky Ball on 2009-02-18
Try ntfs-3g. It is in the repos. Install then run it from the System menu. (NTFS Configuration Tool). That will re-write things for you. :)

---

### Post by drs305 on 2009-02-18
This should work. NTFS mounts are registered as fuseblk but we use ntfs (or ntfs-3g) in fstab:
```

/dev/sda2  /media/local  ntfs  rw,exec,auto,user,sync  0  0

```

---

### Post by yther on 2009-02-18
Instead of "fuseblk" try "ntfs-3g".  For example, here's how I mount my Vista drive when booted to Kubuntu:

```
/dev/sda3       /mnt/Vista      ntfs-3g    noexec  0 0
```

---

### Post by Arch_NME on 2009-02-18
I installed that NTFS configuration tool as Bucky Ball suggested.

It worked!! :D

Here is the lines it added to my **fstab**
```

/dev/sda2 /media/Local ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/XP ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Thanks for the quick reply everyone.

---

