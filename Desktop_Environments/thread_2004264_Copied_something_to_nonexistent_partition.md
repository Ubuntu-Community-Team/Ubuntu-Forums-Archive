---
title: "Copied something to nonexistent partition"
date: 2012-06-15
forum: Desktop Environments
---

### Post by cosners on 2012-06-15
Okay, so I was following the instructions on the Gentoo Linux LiveUSB how-to and it told me to execute 
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdc

(I changed share to lib when I did this because that's where I found syslinux, but this isn't particularly relevant)

My flash drive is actually /dev/sdb1 but I forgot to change that around at the time. It apparently copied it successfully, giving me this message:
```

0+1 records in
0+1 records out
440 bytes (440 B) copied, 0.0297745 s, 14.8 kB/s

```

So what exactly did I just do, and is it bad?
fdisk -l tells me that there is no /dev/sdc

---

### Post by AnotherMuggle on 2012-06-15
> **cosners said:**
> Okay, so I was following the instructions on the Gentoo Linux LiveUSB how-to and it told me to execute 
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdc

(I changed share to lib when I did this because that's where I found syslinux, but this isn't particularly relevant)

My flash drive is actually /dev/sdb1 but I forgot to change that around at the time. It apparently copied it successfully, giving me this message:
```

0+1 records in
0+1 records out
440 bytes (440 B) copied, 0.0297745 s, 14.8 kB/s

```

So what exactly did I just do, and is it bad?
fdisk -l tells me that there is no /dev/sdc

Please post output of:
```
sudo fdisk -l
```

the sudo could be important, without it I see no output at all.

---

### Post by cosners on 2012-06-15
Here it is.
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019569

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484222975   242110464   83  Linux
/dev/sda2       484225022   488396799     2085889    5  Extended
/dev/sda5       484225024   488396799     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders, total 3940351 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3940350     1970159+   e  W95 FAT16 (LBA)

```

Also, I seem to have posted this in the wrong place. I'd appreciate it if a mod could move this to "general help".

Edit: I re-read what you said and now I see what you mean. I DID run it with sudo, but I forgot to mention this at the beginning of the thread. Still, posting the output of fdisk can't hurt.

---

### Post by AnotherMuggle on 2012-06-15
> **cosners said:**
> Here it is.
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019569

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484222975   242110464   83  Linux
/dev/sda2       484225022   488396799     2085889    5  Extended
/dev/sda5       484225024   488396799     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders, total 3940351 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3940350     1970159+   e  W95 FAT16 (LBA)

```

Also, I seem to have posted this in the wrong place. I'd appreciate it if a mod could move this to "general help".

Edit: I re-read what you said and now I see what you mean. I DID run it with sudo, but I forgot to mention this at the beginning of the thread. Still, posting the output of fdisk can't hurt.

Strange.  Basically what you asked dd to do was to copy syslinux to the MBR of device sdc, but since it's not there I don't know what the defined behaviour of dd should be.  I checked the man pages and can't see anything to clarify.  Maybe someone else can answer...

If you want to try again then you need to write to device sdb, not sdb1 which is a partition rather than the MBR.

Your command should look like this:
```
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdb
```

EDIT: On second thought take a look in /dev and see if here is a file called sdc, dd might have just created the output file there!?

---

### Post by cosners on 2012-06-15
> **AnotherMuggle said:**
> 
Your command should look like this:
```
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdb
```

EDIT: On second thought take a look in /dev and see if here is a file called sdc, dd might have just created the output file there!?

Thanks, I'll fix it! Also, looks like the command DID create an output file called sdc. I'll leave it alone for now since it doesn't seem to be harming anything.

---

