---
title: "mounting partitions RW at boot"
date: 2009-01-10
forum: General Help
---

### Post by anafshalom on 2009-01-10
I just installed Ubuntu I have a couple of problems:

I've been using Fedora core6, and I'm trying out Ubuntu.

I had my Home on its own partition. I tried to use this same partition as the home for Ubuntu, but could not figure that out, so I have the Home for Ubuntu in another partition. I want to have the Fedora home partition mounted RW so I can keep the files I use syncronized without having to be a super user.

For some reason some of the partitions are not mounting at boot up, and when I do a mount -a they mount, but they are read-only.

The other problem I have, is that I do not remember the root password I used when I installed Ubuntu

Here is the fstab as it reads now:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda4
UUID=d5053608-2763-42f0-ab9b-90e98199789c / ext3 relatime,errors=remount-ro 0 1

/dev/sda2 /home/FedoraRoot ext3 defaults 0 0

/dev/sda5 /home/E vfat rw,user,auto 0 0

# /dev/sda6
UUID=fdddc7c6-d7c2-4ccd-8854-f1f038a714a3 none swap sw 0 0

/dev/sda7 /home/FedoraHome ext2 auto,user,rw 0 2

/dev/sda8 /home/D vfat auto,user,rw 0 0

# /dev/sda9
UUID=9f1c3764-6aa1-4745-ab7f-70f92d8c5301 /home ext3 relatime 0 2

# /dev/sda10
UUID=a068755a-bbec-4d94-b4ec-46b098de81d0 /home/g ext3 relatime 0 2


/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by dcstar on 2009-01-10
> **anafshalom said:**
> 
.........
For some reason some of the partitions are not mounting at boot up, and when I do a mount -a they mount, but they are read-only.

The other problem I have, is that I do not remember the root password I used when I installed Ubuntu
.........

Tell us which partitions aren't mounting RW and we might be able to help.

There is no "root" password on installation, root is disabled by default for security reasons and you use the user password you installed with for sudo access. There are forum posts on enabling the root account (if you must).

---

### Post by sisco311 on 2009-01-10
by default, the root account is disabled in ubuntu.
you can use
```
sudo *command* #su -c *command*
```
or
```
gksu *guiapp*
```
to run an application as root.

to start a root shell:
```
sudo -i #su -
sudo -s #su
```

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

the entry for /home should go before the other entries.

use the uuid to mount the partitions.

[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda4
UUID=d5053608-2763-42f0-ab9b-90e98199789c / ext3 relatime,errors=remount-ro 0 1

[B]# /dev/sda9
UUID=9f1c3764-6aa1-4745-ab7f-70f92d8c5301 /home ext3 relatime 0 2
[/B]

/dev/sda2 /home/FedoraRoot ext3 defaults 0 0

/dev/sda5 /home/E vfat rw,user,auto 0 0

# /dev/sda6
UUID=fdddc7c6-d7c2-4ccd-8854-f1f038a714a3 none swap sw 0 0

/dev/sda7 /home/FedoraHome ext2 auto,user,rw 0 2

/dev/sda8 /home/D vfat auto,user,rw 0 0


# /dev/sda10
UUID=a068755a-bbec-4d94-b4ec-46b098de81d0 /home/g ext3 relatime 0 2


/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

to mount the fat partitions with rw permissions try something like:
> UUID=xyz.. /mount/point vfat defaults,umask=007,gid=46 0 0

---

### Post by anafshalom on 2009-01-10
I just rebooted.  (solved root password issue)

These are not mounting:
sda2   /home/FedoraRoot	ext3	defaults	0	0
sda5   /home/E	        vfat	rw,user,auto	0	0
sda7   /home/FedoraHome ext2 auto,user,rw	0	2
sda8   /home/D	vfat	auto,user,rw		0	0


here is the output of mount:

/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda9 on /home type ext3 (rw,relatime)
/dev/sda10 on /home/g type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/reuven/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=reuven)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by taurus on 2009-01-10
What are the outputs of these commands?

```
sudo fdisk -l
sudo blkid
```

---

### Post by anafshalom on 2009-01-10
> **taurus said:**
> What are the outputs of these commands?

```
sudo fdisk -l
sudo blkid
```


root@ubuntu:/home/reuven# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e66b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         655     5261256    b  W95 FAT32
/dev/sda2             656        1675     8193150   83  Linux
/dev/sda3            2406        4865    19759950    f  W95 Ext'd (LBA)
/dev/sda4   *        1676        2405     5863725   83  Linux
/dev/sda5            3863        4736     7020405    b  W95 FAT32
/dev/sda6            4737        4865     1036161   82  Linux swap / Solaris
/dev/sda7            3328        3862     4297356   83  Linux
/dev/sda8            2917        3327     3301294+   b  W95 FAT32
/dev/sda9            2406        2814     3285229+  83  Linux
/dev/sda10           2815        2916      819283+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4060 MB, 4060086272 bytes

root@ubuntu:/home/reuven# blkid
/dev/sda1: LABEL="WIN-BOOT" UUID="383A-1311" TYPE="vfat" 
/dev/sda2: LABEL="/" UUID="e6f1f34b-db68-4873-baef-3f20d73922e9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="d5053608-2763-42f0-ab9b-90e98199789c" TYPE="ext3" 
/dev/sda5: LABEL="DRIVERS" UUID="9FC3-09B6" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="fdddc7c6-d7c2-4ccd-8854-f1f038a714a3" 
/dev/sda7: UUID="bf54ecb3-3cda-46b2-bd39-2145f861a36b" TYPE="ext2" 
/dev/sda8: UUID="4770-7B2F" TYPE="vfat" 
/dev/sda9: UUID="9f1c3764-6aa1-4745-ab7f-70f92d8c5301" TYPE="ext3" 
/dev/sda10: UUID="a068755a-bbec-4d94-b4ec-46b098de81d0" TYPE="ext3" 
/dev/sdb1: UUID="0000-0BF8" TYPE="vfat" 

I am in the process of changing fstab to reference UUIDs

---

### Post by anafshalom on 2009-01-10
I made all of the partitions mount using UUIDs in the fstab, and they all mounted!  
BUT the ones that did not mount automatically before are still read only:

Here are the current fstab lines:
#/dev/sda2
UUID=e6f1f34b-db68-4873-baef-3f20d73922e9 /home/FedoraRoot	ext3	defaults	0	0
#/dev/sda5
UUID=9FC3-09B6				/home/E	  vfat	rw,user,auto			0	0
# /dev/sda6
UUID=fdddc7c6-d7c2-4ccd-8854-f1f038a714a3 none     swap    sw              		0	0
#/dev/sda7
UUID=bf54ecb3-3cda-46b2-bd39-2145f861a36b /home/FedoraHome ext2	 auto,user,rw		0	2
#/dev/sda8
UUID=4770-7B2F				/home/D	vfat	auto,user,rw			0	0

---

### Post by taurus on 2009-01-10
[http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32](http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32)

---

