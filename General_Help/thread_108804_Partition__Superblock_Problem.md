---
title: "Partition / Superblock Problem"
date: 2005-12-27
forum: General Help
---

### Post by matthinckley on 2005-12-27
OK I have problems that I have no clue how to fix.. but I'm a quick learner if somebody could steer me in the right direction..

Here's what I have

160 GB Hard Drive

originally had only ubunto on it with the following partitions (direct from fstab)

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /mnt/storage    ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

OK now I am setting up another computer as a battlefield 1942 server and I had to put WinXP on this computer to play since I have an ATI video card right now, until I get an nVidia card so I can use cedega...

So I used the live cd and parted to resize the /dev/hda1 partition from 60 to 30 GB then installed windows formatting the new space to FAT32.  windows works fine.

Obviously WinXP rewrote the MBR with its boot loader so I used the install cd and rescue mode to 'grub-install /dev/hda'

Grub back in.. great, now here is where the problems start

as Ubuntu is booting, when It got to checking all file systems it hiccuped.. badly.. It gave me an error about /dev/hda6 not existing.. this is bad.. this is my 100GB partition that holds all my music and movies.. don't want to lose this one.. So I open up fstab and comment out /dev/hda6.. ubuntu boots.

OK so where did my movies go?  I run parted and try to print my partition list and it gives me this error:

```
Error: Unable to satisfy all constraints on the partition.
```

I'm totally lost now.. starting to freak out a little bit but I know the stuff has to still be on the hard drive, I just have to figure out how to get it..

So now I run fdisk -l :

```
omitting empty partition (5)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3556    28563538+  83  Linux
/dev/hda2   *        3557        7112    28563570    c  W95 FAT32 (LBA)
/dev/hda3            7113       19457    99161212+   5  Extended
/dev/hda4           19270       19457     1510078+  82  Linux swap / Solaris
/dev/hda5            7113       19269    97651039+  83  Linux
```

this is weird.. I don't have /dev/hda6 at all that fstab is looking for.. and /dev/hda5 isn't swap, /dev/hda4 is.. so at this point I decide to try mounting /dev/hda5 as /mnt/storage and low and behold.. there are my movies and my music.. GREAT!  ok so now I suppose I can just edit fstab to fix the differences. but I'm still having this error in parted.. I ran fsck from the live cd and it said everything was clean, but it's the partition table that's messed up and I don't know how to fix that.. 

Thanks for any help

Matt

---

