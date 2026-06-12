---
title: "GRUB Error 17  Ubuntu 8.0.4"
date: 2009-05-14
forum: General Help
---

### Post by opholdings on 2009-05-14
One year old Ubuntu 8.0.4 installation.  Only Ubuntu is loaded on the machine. Tried starting machine today and received the dreaded error:

Grub 1.5
Error 17

Tried the Vista and XP with Ubuntu fix:

From Live CD

sudo grub
find /boot/grub/stage1

This did not return results.  Just Error 15.

Any suggestions?

---

### Post by Egi_Power on 2009-05-14
> **opholdings said:**
> From Live CD

sudo grub
find /boot/grub/stage1

This did not return results. Just Error 15.

When you installed Ubuntu, did you make a separate partition for /boot?
I have on my laptop the /boot on a separate partition and I got the same error for
```
sudo grub
find /boot/grub/stage1
```

However, it worked leaving out /boot from the command
```
sudo grub
find /grub/stage1
```

Give it a try and write any error you get.

Best regards,

Egi_Power

---

### Post by opholdings on 2009-05-14
Thanks EP.

Tried all of the combinations at the terminal.  Sudo and all.

All suggestions surely welcome.

Forgot the error:

Error 15: File not found.

---

### Post by unutbu on 2009-05-14
opholdings, please run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt file here.

---

### Post by opholdings on 2009-05-14
Here is the results.txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb88863e4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: TYPE="swap" UUID="abed913d-7626-4410-adb2-46d72723a89b" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  a4 81 00 00 64 90 00 00  f9 9a 0a 4a 87 f0 55 48  |....d......J..UH|
00000010  9c d8 eb 47 00 00 00 00  00 00 01 00 50 00 00 00  |...G........P...|
00000020  00 00 00 00 00 00 00 00  58 28 2c 00 59 28 2c 00  |........X(,.Y(,.|
00000030  5a 28 2c 00 5b 28 2c 00  5c 28 2c 00 5d 28 2c 00  |Z(,.[(,.\(,.](,.|
00000040  5e 28 2c 00 5f 28 2c 00  60 28 2c 00 61 28 2c 00  |^(,._(,.`(,.a(,.|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 db e9 c3 a6  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  ff a1 00 00 12 00 00 00  84 e5 00 4a 87 f0 55 48  |...........J..UH|
00000090  87 f0 55 48 00 00 00 00  00 00 01 00 00 00 00 00  |..UH............|
000000a0  00 00 00 00 00 00 00 00  6c 69 62 62 72 6c 61 70  |........libbrlap|
000000b0  69 2e 73 6f 2e 30 2e 35  2e 31 00 00 00 00 00 00  |i.so.0.5.1......|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  00 00 00 00 dc e9 c3 a6  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  a4 81 00 00 b8 80 00 00  04 f8 c9 48 87 f0 55 48  |...........H..UH|
00000110  e2 2c ec 47 00 00 00 00  00 00 01 00 48 00 00 00  |.,.G........H...|
00000120  00 00 00 00 00 00 00 00  62 28 2c 00 63 28 2c 00  |........b(,.c(,.|
00000130  64 28 2c 00 65 28 2c 00  66 28 2c 00 67 28 2c 00  |d(,.e(,.f(,.g(,.|
00000140  68 28 2c 00 69 28 2c 00  6a 28 2c 00 00 00 00 00  |h(,.i(,.j(,.....|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 dd e9 c3 a6  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  ff a1 00 00 0f 00 00 00  84 e5 00 4a 87 f0 55 48  |...........J..UH|
00000190  87 f0 55 48 00 00 00 00  00 00 01 00 00 00 00 00  |..UH............|
000001a0  00 00 00 00 00 00 00 00  6c 69 62 62 7a 32 2e 73  |........libbz2.s|
000001b0  6f 2e 31 2e 30 2e 34 00  00 00 00 00 00 00 00 00  |o.1.0.4.........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 de e9 c3 a6  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by unutbu on 2009-05-14
opholdings, the RESULTS.txt file shows there is problem mounting /dev/sda1, your Linux partition. This suggests there is filesystem corruption. Do you know what might have caused this? (e.g. abruptly turning off the machine, or a power outage?)

After booting from the LiveCD, how about try this:

```
sudo umount /dev/sda1    # Don't worry if this says sda1 is not mounted
sudo e2fsck -C0 -pfv /dev/sda1
```

You may get an error message after running this command. Maybe
```

e2fsck: Bad magic number in super-block while trying to open /dev/sda1
``` or```

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options). 
```
Post back with what output you get and we will try to help. Also, it would be beneficial to read [http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem) (search for "Running a filesystem check on an ext3  filesystem").

---

### Post by opholdings on 2009-05-14
Tried: 

```
sudo umount /dev/sda1    # Don't worry if this says sda1 is not mounted
sudo e2fsck -C0 -pfv /dev/sda1
```

Here is the result of the terminal commands:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -C0 -pfv /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I will start reading the superblock info from the link you provided and provide additional information.

The machine hung after a quick update and needed a hard reboot.  The probable cause.  I have it set to check the disk every 30 boots.


The results from the Superblock repair tutorial. My knowledge of terminal commands is limited and may require assistance.

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -C0 -pfv /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ dumpe2fs /dev/hda5
dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: No such file or directory while trying to open /dev/hda5
Couldn't find valid filesystem superblock.
ubuntu@ubuntu:~$ e2fsck -b 32768 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e2fsck -b 8193
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 32768
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 32768 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$  e2fsck -b 32768
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$  e2fsck -b -p 32768

Invalid non-numeric argument to -b ("-p")

ubuntu@ubuntu:~$  e2fsck -bp 32768

Invalid non-numeric argument to -b ("p")

ubuntu@ubuntu:~$  e2fsck -b 98304
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$  e2fsck -b 98304 -p
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 98304 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e2fsck -b 98304 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e2fsck -b 98304 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e2fsck -b 163840
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 229376 /dev/hda5
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e2fsck -b 229376 /dev/hda1
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 8193
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b 8193
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -f
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ e2fsck -b-v 8193

Invalid non-numeric argument to -b ("-v")

ubuntu@ubuntu:~$ e2fsck -v
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ dumpe2fs /dev/hda5
dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: No such file or directory while trying to open /dev/hda5
Couldn't find valid filesystem superblock.

```

---

