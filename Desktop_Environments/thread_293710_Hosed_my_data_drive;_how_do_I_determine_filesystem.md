---
title: "Hosed my data drive; how do I determine filesystem blocksize?"
date: 2006-11-05
forum: Desktop Environments
---

### Post by Terry of Astoria on 2006-11-05
I'm running breezy and I hosed my data storage drive with a power control failure.(Improper shutdown!) My 250 G WD hard drive /dev/hdd that has various partitions including FAT32, ext3, and NTFS is not mounted at boot. 

I typed fsck and hit enter (see):
```
me@maestro:~$ fsck -n /dev/hdd
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdd

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
Now I want to do that, but I want to be careful to do it right. To specify the alternate superblock properly I need to know the blocksize of the filesystem. **How do I find out the filesystem blocksize? Am I on the right track?** Any other suggestions? I'll put my fstab here.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1       /mnt/win_c  vfat    iocharset=utf8,umask=000   0       0
/dev/hdd1       /mnt/win_d  vfat    iocharset=utf8,umask=000   0       0
/dev/hdd5       /mnt/linuxdata      ext3    defaults,errors=remount-ro 0   0
/dev/hdd3       /mnt/ntfs   ntfs    nls=utf8,umask=0222 0       0

```
Thanks.

---

### Post by bsussman on 2006-11-05
Since hdd is a disk and not a filesystem, I would not be expecting to see anything of use by running fsck on it.

Try running gparted and inspect the disk to see what partitions there are and then carefully fsck them.

If you are more comfortable at the command line, use fdisk or parted.  parted has a help command. 

One clue: files systems have 4 characters in the name: /dev/hda1 or /dev/sdb2 etc.

It is unusual for a power event to take out a whole disk and leave the hardware useable.

BTW, the command for finding blocksize is dumpe2fs and it also requires a filesystem, not a disk as input.  Pipe its output thru less or to a file since the block chain dump will fill your terminal buffer and you will not be able to backscroll to the good stuff.

You may not have lost anything.

Go slowly.

---

### Post by Terry of Astoria on 2006-11-05
Thanks for your interest.
See the following output from fdisk -l
Yes. I still get the bad superblock message when I specify the patition though.
I'll try what you suggested. 
Thanks again.
```
me@maestro:~$ fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1020     8193118+   b  W95 FAT32
/dev/hda2   *        1021        4704    29591730   83  Linux
/dev/hda3            4705        4865     1293232+   5  Extended
/dev/hda5            4705        4865     1293201   82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   ?           1        8796    70653838+   c  W95 FAT32 (LBA)
/dev/hdd2            8797       24093   122873152+   5  Extended
/dev/hdd3           24094       30401    50669010    7  HPFS/NTFS
/dev/hdd5            8797       24093   122873121   83  Linux

```

---

### Post by bsussman on 2006-11-05
Odd - it says it doesnt look like a partition table and then prints partition table info....

1.  This is bad,. be prepared to lose it all.  Then if you recover it you can party.

2. Write down the begin/end blocks and fstypes for possible reconstruction.

3. Try to repair with fsck.  Maybe try booting Windows to see how it feels about the win partitions.

4. Desparate! Try re-making partition table with parted or fdisk.

5.  Go slow and ask questions.

6.  Be prepared to lose everything!

---

### Post by Terry of Astoria on 2006-11-05
Parted did something when I did the rescue function, but my entire drive was still inaccessible and unmountable. fdisk couldn't help, evemn after I provided the locations of backup superblocks. Then while reading on wikipedia I discovered a GPL program called testdisc and ran that. Following the their directions, I was able to recover all my data.
   Thank you bsussman for your help. Without your encouragement I may not have done it.
   Also, please everyone do backups! Now!
   Aloha Nui Loa

---

### Post by bsussman on 2006-11-06
> **Terry of Astoria said:**
> Then while reading on wikipedia I discovered a GPL program called testdisc and ran that. Following the their directions, I was able to recover all my data.
Aloha Nui Loa

Cool - now change the thread name to include (solved) and post where you found this particular tool.  :-D

---

### Post by jhenager on 2006-11-06
> **bsussman said:**
> Cool - now change the thread name to include (solved) and post where you found this particular tool.  :-D

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
This program looks awesome.

"TestDisk can run under

    * DOS (either real or in a Windows 9x DOS-box),
    * Windows (NT4, 2000, XP, 2003),
    * Linux,
    * FreeBSD, NetBSD, OpenBSD,
    * SunOS and
    * MacOS 

Source files and precompiled binary executables are available for DOS, Win32, MacOSX and Linux from the download page"

---

### Post by Terry of Astoria on 2006-11-06
Thanks very much. I love this forum. 
Here is where I found testdisk. [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
Anyone know of another program that makes it easy to edit partition tables? I love open source!

---

### Post by Terry of Astoria on 2006-11-06
Yes. It worked well for me. In my desperation to repair my filesystem I used testdisk to change my ext3 data partition from a logical partition into a primary partition. After writing my new partition table, I rebooted and was able to fsck and mount my partition. Funny tho- while the disc was "hosed" testdisc didn't seem to see anything wrong except that after searching for partitions it no longer showed the containing extended partition, only the ext3 partition inside, although it correctly marked it logical. However, The Simpsons was going to be on in 15 minutes, and I "winged it" and decided to change the status of that partition to primary, and it worked. I've learned a lot today, not the least of which was a lesson I sure ought to have learned a long time ago- back up your data!
> Cool - now change the thread name to include (solved) and post where you found this particular tool.
Sorry but don't know how to do that. I tried, and I tried to find help on the forum site, but it wasn't very apparent. Also I can't seem to find where I change my profile details. I'm tired. Love ya. Bye.

---

