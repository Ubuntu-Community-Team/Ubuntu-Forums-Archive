---
title: "How to fix partitions and make bootable Windows again ?"
date: 2009-03-23
forum: General Help
---

### Post by chngr on 2009-03-23
Hi all,
A couple weeks ago, I decided to install Ubuntu so repartitoned the disk with Paragon Partition Manager. Somehow It failed up, and I couldnt boot into Windows anymore so I install Ubuntu from a Live CD and let it repartition my drive. Succesfully intalled ubuntu.

My problem is getting my partitions back and boot into windows xp.
I'm using testdisk and see the files in that partition and I am able to copy it so the files is not corrupted. I tried every method; using testdisk, fixboot fixmbr from Windows restore cd, gparted, reinstalled an reconfigured grub and menu.lst.
Repaired window by using XP cd. But I can't solve this issue. Here is some information about it.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01c001c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189        7588    35343000    f  W95 Ext'd (LBA)
/dev/sda3            7589        7828     1927800   82  Linux swap / Solaris
/dev/sda4            7829        9729    15269782+  83  Linux
/dev/sda5            7283        7559     2224971   82  Linux swap / Solaris

```The following is testdisk output
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3187 254 63   51215157
D HPFS - NTFS           3187  16  1  7281 254 63   65785167
L Linux Swap            7282   1  1  7558 254 63    4449942
* Linux Swap            7588   0  1  7827 254 63    3855600
P Linux                 7828   0  1  9728 254 63   30539565

```

Here is a portion of my menu.lst
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		78ba1c0b-112b-4834-aef1-2c5370b1f452
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78ba1c0b-112b-4834-aef1-2c5370b1f452 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		78ba1c0b-112b-4834-aef1-2c5370b1f452
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78ba1c0b-112b-4834-aef1-2c5370b1f452 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		78ba1c0b-112b-4834-aef1-2c5370b1f452
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,1)
makeactive
chainloader +1

```

And this is the parted's [screenshot]("http://img14.imageshack.us/img14/8425/screenshotccn.png").

It seems I have two primary partition.
It is really making me angry and I am thinking FORMAT entire disk. Anyone has any opinion ? Is it possible to fix it.

Note: Sorry for my poor grammar. I am not a native speaker of English. I also sorry for such a long post :)

---

### Post by CoximusPrime on 2009-03-23
hi chngr,

  I'm not sure if I can help here but someone might be able to tell you if this is a viable solution (I wouldn't recommend trying it until you have some more feedback on it though).

  In the past when I have installed linux on a disk and then want to put windows back on, I've had to use a windows boot disk and use the command "fdisk /mbr" ... That has then allowed me to repartition and install windows on the drive again. 

  I'm not sure if this is what you are trying to do, or whether you are trying to recover the existing XP partition, but googling for fdisk /mbr might point you in a good direction ... not sure if this will help but if it does, that's my good deed done for the day :)

---

### Post by angelsguitar on 2009-03-23
When you try to boot, what do you get? Any error message?  Do you still have grub or did you overwrite it with fdisk /mbr?

---

### Post by chngr on 2009-03-23
I get "Error 12 : Invalid Device Requested" error. And I didnt fdisk /mbr. I used fixmbr instead, fixmbr alseo deletes MBR records, doesnt it?
Should I use fdisk /mbr ? 
And Yes I still have GRUB but lots of times I did fixmbr and lost it then reinstall GRUB.

---

### Post by angelsguitar on 2009-03-23
Ok, another thing I noticed: your win xp partition is on /dev/sda1, am I right? But your menu.lst entry for Windows (the one at the end) says it is looking for that partition on hd0,1 . It should say (hd0,0), since grub starts numbering partitions at 0 not 1, and sda1 is the first partition. Try changing this section in menu.lst:

```

title Windows XP
root (hd0,1)
makeactive
chainloader +1

```

to this - basically change (hd0,1) to (hd0,0):

```

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```

Save the changes at see if it solves your problem.

---

### Post by chngr on 2009-03-23
> **angelsguitar said:**
> Ok, another thing I noticed: your win xp partition is on /dev/sda1, am I right? But your menu.lst entry for Windows (the one at the end) says it is looking for that partition on hd0,1 . It should say (hd0,0), since grub starts numbering partitions at 0 not 1, and sda1 is the first partition. Try changing this section in menu.lst:
Save the changes at see if it solves your problem.

Yes You were right, I changed it and rebooted.
It says "Starting Up" that is it. I didnt boot, even HD led was not on.

Somewhere on the Internet, I read an article that says if you have two primary partition and GRUB is not installed Windows' partition, You must copy some system files such as ntdetect...( I cant remember) into linux partition bla bla bla....
I never found that again :D
Do you think it is possible ?

---

### Post by angelsguitar on 2009-03-23
> **chngr said:**
> Yes You were right, I changed it and rebooted.
It says "Starting Up" that is it. I didnt boot, even HD led was not on.

Somewhere on the Internet, I read an article that says if you have two primary partition and GRUB is not installed Windows' partition, You must copy some system files such as ntdetect...( I cant remember) into linux partition bla bla bla....
I never found that again :D
Do you think it is possible ?

Mmm...Never heard of that.  I have a similar configuration in my laptop (a recovery partition on sda1 for Vista, and the Vista partition on sda2, plus a few other partitions for other linux distros) and never had to do anything like that.

I believe there's something wrong with your Win XP partition (maybe it was messed up when you used the partition manager you mentioned in the first post?).  Try these options:

1) Maybe the partition manager you used installed some kind of propietary driver to load - not sure as I don't know that partition manager. Try the fdisk /mbr and see if that gets you booting Win XP again.  If it works, then reinstall grub.  Here's a good guide I've used before successfully to reinstall it using the Ubuntu LiveCD:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

2) If that doesn't work, you may try to reinstall Windows, and then reinstall grub to the mbr using the guide above.

---

