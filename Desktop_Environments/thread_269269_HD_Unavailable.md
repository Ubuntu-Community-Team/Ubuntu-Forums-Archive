---
title: "HD Unavailable?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Rayston on 2006-10-01
One of my secondary HD's is suddenly unavailable, it is listed in DISKS but it is unavailable and when I click Enable, it has no affect. 

How do I figure out whats wrong? What Diagnostic tools are at my disposal for such a problem?

Thank you 

Del Benjamin

---

### Post by orb9220 on 2006-10-01
Post your fstab here with a command of:  gedit /etc/fstab :in a teminal.
And copy and paste here.

---

### Post by Rayston on 2006-10-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mount/sda1               ext2    exec,rw,errors=remount-ro 0       1
/dev/hdc1       /mount/hdc1               ext3    exec,rw,errors=remount-ro 0       1



its the hdc1 thats not showing up.

---

### Post by Rayston on 2006-10-01
Okay, I talked to a helpful guy on the ubuntu IRC chat and he advised trying to manually mount. I got the below. 

sudo mount -t ext2 /dev/hdd /mount/hdc1

mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I switched around the cables at one point and I think the hard drive is now hdd instead of hdc1

Any ideas?

---

### Post by Rayston on 2006-10-01
Okay, I switched around the cables again, and now the device is dev/hdc

rayston@Rayston:~$ sudo mke2fs -n /dev/hdc
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
1221600 inodes, 2442636 blocks
122131 blocks (5.00%) reserved for the super user
First data block=0
75 block groups
32768 blocks per group, 32768 fragments per group
16288 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632


I tried starting with alternative using this command 

e2fsck -f -b 8193 /dev/hdc

and got this response 

e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/hdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I try with ALL various alternative superblocks and either get the above Bad magic number error or get the following 

rayston@Rayston:~$ sudo e2fsck -f -b 1605632 /dev/hdc
e2fsck 1.38 (30-Jun-2005)
e2fsck: Invalid argument while trying to open /dev/hdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Invalid Argument? what does that mean&#65311;

---

### Post by Rayston on 2006-10-02
Any help on this? 

Do I just have to reformat the drive and start over?

---

