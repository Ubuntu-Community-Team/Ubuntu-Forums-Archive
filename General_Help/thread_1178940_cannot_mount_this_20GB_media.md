---
title: "cannot mount this 20GB media?"
date: 2009-06-05
forum: General Help
---

### Post by abhilashm86 on 2009-06-05
i only have ubuntu 8.04, no windows, i've 80 GB hard drive,
i've divided 80 GB into 4 equal partitions 20GB each,
problem is in /etc/fstab i cannot include /dev/sda1 why is this error?
this drive wont automount on startup,

```
abhilash@abhilash:~$ sudo blkid
/dev/sda1: UUID="5AB85F79B85F529D" TYPE="ntfs" 
/dev/sda6: UUID="c098dd08-8b82-4dd6-b2b1-fff959ab7870" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="53b39459-d52d-4d6a-bdb2-1e6bfcabfb36" 
/dev/sda8: LABEL="SONGS" UUID="71B1-0D79" TYPE="vfat" 
/dev/sda9: LABEL="MUSIC" UUID="DCC5-0AE8" TYPE="vfat" 
abhilash@abhilash:~$ 
abhilash@abhilash:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              18G  8.6G  7.9G  53% /
varrun                187M  112K  187M   1% /var/run
varlock               187M     0  187M   0% /var/lock
udev                  187M   60K  187M   1% /dev
devshm                187M   12K  187M   1% /dev/shm
lrm                   187M   39M  148M  21% /lib/modules/2.6.24-23-generic/volatile
/dev/sda8              19G   11G  8.5G  55% /media/songs
/dev/sda9              19G   11G  8.0G  58% /media/music
gvfs-fuse-daemon       18G  8.6G  7.9G  53% /home/abhilash/.gvfs

```

the contects of /etc/fstab is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c098dd08-8b82-4dd6-b2b1-fff959ab7870 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=53b39459-d52d-4d6a-bdb2-1e6bfcabfb36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=71B1-0D79 /media/songs vfat iocharset=utf8,umask=000 0 0 

UUID=DCC5-0AE8 /media/music vfat iocharset=utf8,umask=000 0 0

UUID=5AB85F79B85F529D /media/disk ntfs iocharset=utf8,umask=000 0 0



```
how should i add to fstab inorder to get /dev/sda1 automount? help pls

---

### Post by merlinus on 2009-06-05
You might try installing ntfs-3g.

---

### Post by abhilashm86 on 2009-06-05
> **merlinus said:**
> You might try installing ntfs-3g.

its already installed, now what exactly i need to do??

---

### Post by merlinus on 2009-06-05
```

sudo apt-get install ntfs-config

```It should appear in Applications/System Tools, and then give you some checkboxes to enable.  Restart, and the appropriate line(s) will be written in /etc/fstab.

---

### Post by abhilashm86 on 2009-06-05
> **merlinus said:**
> ```

sudo apt-get install ntfs-config

```It should appear in Applications/System Tools, and then give you some checkboxes to enable.  Restart, and the appropriate line(s) will be written in /etc/fstab.

ya thanks ,it recognised ntfs disk, it also asked,
enable write support for external device, what it means, should i enable it?

---

### Post by merlinus on 2009-06-05
You do not need it unless you have a USB external hdd, or perhaps a flash drive formatted as ntfs.  OTOH, it will not hurt to enable it.

---

### Post by abhilashm86 on 2009-06-05
> **merlinus said:**
> You do not need it unless you have a USB external hdd, or perhaps a flash drive formatted as ntfs.  OTOH, it will not hurt to enable it.

oh thanks so much, i got the meaning:)

---

