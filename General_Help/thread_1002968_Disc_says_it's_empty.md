---
title: "Disc says it's empty"
date: 2008-12-05
forum: General Help
---

### Post by Secession on 2008-12-05
I have two discs.  The one Linux runs from is fine but the other one is being odd.  After the machine has been on for about half a day if I try to list the files on the disc it says it's empty.  If I reboot the disc works normally again.

Before I start swapping bits out is there a way to point myself in the right direction?  Can I find out why the files are disappearing?

---

### Post by taurus on 2008-12-05
When you say disc, I assume you mean disk as in harddrive?

What filesystem is that harddrive and how do you mount it?  Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Secession on 2008-12-05
Yes a disc.  A silver coloured box with wires coming out for storing data. ;)  After more sniffing about I found

fsck -rfv /dev/sdb1

which I'm running (it says it's running e2fsck, means EXT2?).  It says I have illegal blocks and multiply claimed blocks and it's fixing them.  It seems very busy.  I suppose if they keep turning up my disc is damaged and I'll replace it.

The result:
/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

     587 inodes used (0.01%)
     413 non-contiguous inodes (70.4%)
         # of inodes with ind/dind/tind blocks: 504/499/0
18137017 blocks used (46.42%)
       0 bad blocks
       1 large file

     539 regular files
      39 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     578 files

I like the "0 bad blocks", I think that's good.

Your commands:

**fdisk -l**

Disk /dev/sda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00880088

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2431      851445    5  Extended
/dev/sda5            2326        2431      851413+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7b6b9b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=6c6b68d7-4570-4e72-8d55-888be1530bb4 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=a0e18042-7a2b-4dbb-87d4-e4e8cc6c8bbc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /mnt/sdb1 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0

**df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  7.7G  9.2G  46% /
varrun                220M  280K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   52K  220M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   39M  182M  18% /lib/modules/2.6.24-22-generic/volatile
/dev/sdb1             148G   69G   73G  49% /mnt/sdb1

---

