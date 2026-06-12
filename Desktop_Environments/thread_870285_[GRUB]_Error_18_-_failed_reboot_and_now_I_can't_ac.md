---
title: "[GRUB] Error 18 - failed reboot and now I can't access my ext3 partition"
date: 2008-07-25
forum: Desktop Environments
---

### Post by pulpfiction on 2008-07-25
Hello,

First of all, this is not a new install and this Ubuntu 7.10 system has been running for more than 6 months. Today it hanged for about 5 minutes after I logged on. I CTRL+ALT+Backspace so I could exit X and try log in again. After a few strange messages with hexadecimals all over it (I admit I should had pay attention to this hint), I tried logon again and it freezed again, this time the screen didn't even change when I pressed <enter> (aka my password as '*******' was still at the screen). I did a hard reboot and then, while booting, GRUB gave me:

```

GRUB loading, please wait...
Error 18

```

I did some research and it seems this error refers to old harddisks. Well, my HD is not old and as I said, it worked just fine for more than 6 months. Actually, it seems the harddisk is just fine, I also have a Windows partition there and, using the Super Grub Disk, I got to boot from it.

I'm now on a Ubuntu 8.04 LiveCD, here's the "fdisk -l" output:

```

$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       14595   106992900    f  W95 Ext'd (LBA)
/dev/sda5            1276       14595   106992868+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d632d62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4866    39078112+   f  W95 Ext'd (LBA)
/dev/sdb5               2        3430    27543411    7  HPFS/NTFS
/dev/sdb6            3431        3554      995998+  82  Linux swap / Solaris
/dev/sdb7            3555        4866    10538608+  83  Linux

```

Ubuntu couldn't mount the partition:

```

$ sudo mount -t ext3 -o ro /dev/sdb7 /media/disk-3
mount: wrong fs type, bad option, bad superblock on /dev/sdb7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So although Ubuntu sees it and lists it on the Places menu, it couldn't mount it:

```

$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

I also tried to run fsck on it, but it didn't work too:

```

$ sudo fsck.ext3 -f /dev/sdb7
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdb7

```

I thought this could be a corrupted superblock, so I tried to run it using a superblock backup:

```

$ sudo mkfs.ext3 -n /dev/sdb7
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
660960 inodes, 2634652 blocks
131732 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2701131776
81 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

$ sudo fsck.ext3 -f -b 98304 /dev/sdb7
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sdb7
Filesystem mounted or opened exclusively by another program?

```

Well, that's all I tried so far. So, does anyone have any other idea how can I recover my ext3 partition?

Thank you!

---

### Post by Neovos on 2008-07-25
Just curious if this happened to you after an update? I let Ubuntu update a bunch of things last night and the first time I rebooted, I got error 18 as well. And my laptop is brand new and had been working for 4 months or more flawlessly.

---

### Post by pulpfiction on 2008-07-25
> **Neovos said:**
> Just curious if this happened to you after an update? I let Ubuntu update a bunch of things last night and the first time I rebooted, I got error 18 as well. And my laptop is brand new and had been working for 4 months or more flawlessly.

Yes, possible. I can't say for sure, but everytime Ubuntu tells me there's an update, I do it. As I recall I did some the last couple of days (just to state again, I was currently running Ubuntu 7.10).

By the way, did you fix yours?

---

### Post by Neovos on 2008-07-26
I've been using hardy on my laptop, so it might not be the same update, but an update non-the-less. The status thus far is that I've managed to create a boot partition in the front of my drive which gets me past the grub error, but I still can't boot any kernels. I copied the /boot info from another Ubuntu comp onto this partition to get it started. Still tweaking it to see if it can't boot because my main partition is dead, or if I just don't have the temp /boot info correct.

What I found is that the error 18 is when the bios can't find the /boot info. My theory as to why this occurred out of the blue is as follows: the computer bios can only read the first 8 gb of the hard drive. So if the /boot info is not there, tough poop. As for my setup, I had 5 gb of swap, then my 250 gb main partition. So I think by chance, my /boot info happened to be in that 3gb sweet zone until now. The only thing I can think happened is that somehow, the os moved that data (or a part of it) to another part of the drive and now it's unaccessible. This would explain error 18.

If not this however, it's possible that the partition itself went bad, or the partition table needs to be rewritten. Correct me if I'm wrong, but in addition to the MBR at the beginning of the drive, we also have a table or header at the start of ever partition right? If the partition went bad, then this could also cause an error 18 because technically, bios can't read this section of drive and can't find the /boot data.

I'm pretty certain for me that my physical hard drive is ok because I've been writing and accessing the other partition on the drive (the new boot partion). But even when I bring up the live cd, I can mount my main partition, but everything hangs when I try to tell it to access any files. This is problematic too because in order to finish the new boot partition, I need to access my old fstab and put it in there. But no can do. So I'm leaning now toward a bad partition (hopefully a bad partition header that can be fixed easily). I need to find a utility to do this.

---

### Post by upchucky on 2008-07-26
drive is fine, bootloader messed. the following is an example from a previous post, search for info if this does not get you happy. this is and installation and upgrade problem and you will get better responses if you repost the problem in that forum.


Code:

sudo fdisk -l

will tell you the partitions, and if hd0,6 looks like it has linux then,


since it found Linux at hd0,6

then do
Code:

sudo grub

then
Code:

find /boot/grub/stage1

it should tell you that root is hd0,6
if this is true,
then do
Code:

setup (hd0,6)

the brackets are part of the code

if it identifies let's say (hd0,1) as root then substitute as needed where i have indicated (hd0,6)

it has shown that root is the mbr bootloader stage1, and the setup tells grub to make a new stage2, stage 2 is the /boot/grub/menu.lst that should get 8.01 running, and if windows will not boot then you need to search for the chainloader info to get it booting

---

