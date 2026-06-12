---
title: "External HD without an OS"
date: 2009-04-23
forum: General Help
---

### Post by texas.chef94 on 2009-04-23
I am still exploring options for use of my external 160 GB HD
How does one utilise an external USB drive for storage alone without installing an OS. 
Another words I merely want to extend the capacity of a 40 GB  internal
with huge amount research data.
Which brings up another question. Must it remain plugged in and what about mounting and unmounting?

Thanks

---

### Post by jsowoc on 2009-04-23
External USB drives, most of the time, do not have an OS installed. They are simply drives used for storing data.

When you plug the USB drive while Ubuntu is running, it should automatically recognize it, mount it, and give you a shortcut on your desktop. You can use this to access the files.

Before you want to turn off/unplug the external drive, be sure to right-click on the shortcut on the desktop and select "unmount". This ensures any pending writes are finished before you unplug it. When a pop-up "device safe to remove" comes up, you can unplug the USB drive and turn it off until you need it again.

---

### Post by texas.chef94 on 2009-04-23
My USB stick work that way, but this 160 GB external does not. I did have an OS installed on it, but presently it is clean resulting from using gparted to delete all partitions. When I plug it in nothing happens on desktop.
Please advise.

Allen

---

### Post by kanikilu on 2009-04-24
You said you "deleted all the partitions", but didn't say if you created any new ones. If not, a drive with no partitions/filesystem is not going to mount.

Open gparted again and create a new partition. Assuming there really is **nothing** on the drive, you can safely create one partition that spans the entire disk. Format the partition as ext3 if you are just going to be using it with Ubuntu, or format it as FAT32 or NTFS if you need to maintain compatibility with Windows.

If you have already created a partition and formatted it, and it *still* doesn't automatically mount, can you post the results of the following commands from a terminal?

```
mount
sudo fdisk -l
ls -l /dev/disk/by-uuid
```

That should give us all the information needed to help you add an entry for the drive in fstab.

---

### Post by texas.chef94 on 2009-04-24
I am giving you terminal results prior to creating a partition and I will give it after as well. I am doing this because in between e-mails it dawned on me that a partition had to me created so I did, but my creativity and just being plain inept I added / to the partition and at reboot I got the error 15. Not having access to forum it next morning re-installed jaunty. Will create the partition as advised and run code again, but will not reboot in hopes someone will advise me should error 15 raise its ugly head again

allen@allen-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/allen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=allen)
allen@allen-desktop:~$ sudo fdisk -1
[sudo] password for allen: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
allen@allen-desktop:~$ ls -1 /dev/disk/by-uuid
7e817119-4c0e-47bc-bbb4-30d25877ce5d
ad4f76e4-7f59-4ac2-abea-4544155dd9b0
allen@allen-desktop:~$ 

This is after creating dev/sdb1/ partition with ext3

allen@allen-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/allen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=allen)
allen@allen-desktop:~$ fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
allen@allen-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-04-24 05:45 6dee4877-aec6-4148-bc3e-dee735bbc14f -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-04-23 22:59 7e817119-4c0e-47bc-bbb4-30d25877ce5d -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-04-23 22:59 ad4f76e4-7f59-4ac2-abea-4544155dd9b0 -> ../../sda1
allen@allen-desktop:~$ 

I repeat I will await a life line before I attempt reboot and thank you so much

---

### Post by megamania on 2009-04-24
> **texas.chef94 said:**
> allen@allen-desktop:~$ fdisk -1
fdisk: invalid option -- '1'

You typed -1 (minus-one) instead of -l (minus-lowercase L)...

---

### Post by texas.chef94 on 2009-04-24
> **megamania said:**
> You typed -1 (minus-one) instead of -l (minus-lowercase L)...

Sorry about that. How about thi. I have not re-booted yet do not want to encounter error 15 again and thanks for calling my attention to my error

Allen

allen@allen-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/allen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=allen)
allen@allen-desktop:~$ sudo fdisk -l
[sudo] password for allen: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c21c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4708    37816978+  83  Linux
/dev/sda2            4709        4865     1261102+   5  Extended
/dev/sda5            4709        4865     1261071   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
allen@allen-desktop:~$

---

### Post by texas.chef94 on 2009-04-24
Ok I have gotten a little further along in this, but still have a ways to go.
With gparted I created a single partition on the external in ext3
1) Create a mount point of your and choose data.
  issue command: mkdir /data so in retrospect:
allen@allen-desktop:~$ mkdir /data
mkdir: cannot create directory `/data': File exists
allen@allen-desktop:~$ 
2) I think I need to create a fstab entry for the new mount point.
    To do this I need edit the /etc/fstab file and enter the
    a line something like this I THINK /dev/sdb1 /data ext3 or some such.
    No clue how to get into this file to edit and kinda scary.
3) If I could do that then I think I Reboot or just sudo mount -a   #or just reboot
4. I want a symlink as well so I still need lots help and hope someone still has enough patience to advise me

Allen

---

### Post by jsowoc on 2009-04-24
You should not need to edit /etc/fstab to have the external drive mount/unmount itself automatically when you plug/unplug it.

Ok, so here is what you have:
/dev/sda1 -> your "main" drive
/dev/sda5 -> your swap space
/dev/sdb1 -> the only partition on the 160 GB external drive

I would assume that while the partition /dev/sdb1 is created, it is not formatted. You need to decide if you will use the drive only on Linux machines, or if you also need to sometimes connect it to Windows machines.

In the Linux-only case, the best file system is ext3. To format /dev/sdb1 as ext3 (you will lose all data on the external drive, if there was any):
sudo mkfs.ext3 /dev/sdb1

In the Linux + Windows case, you have the option of using vfat or ntfs. I suggest vfat:
sudo mkfs.vfat /dev/sdb1

After you execute one of the above "mkfs" commands on the external drive, it should automatically mount.

---

### Post by jsowoc on 2009-04-24
To answer your question about symbolic links, you seem to want your files in /data. By default, the drive is mounted in /media, in a sub-folder with the name of the partition. To give the partition a name when formatting, the command would be one of:

sudo mkfs.ext3 -L research /dev/sdb1
sudo mkfs.vfat -n research /dev/sdb1

You can then remove the folder /data, and create a symbolic link to where you need, for example:
sudo ln -s /media/research /data

---

### Post by texas.chef94 on 2009-04-24
Does this mean I am home free and it ended with this

allen@allen-desktop:~$ sudo mkfs.ext3 /dev/sdb1
[sudo] password for allen: 
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
9773056 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 238878

---

### Post by jsowoc on 2009-04-24
Now check to see if anything appeared in /media/disk

---

