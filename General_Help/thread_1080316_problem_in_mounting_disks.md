---
title: "problem in mounting disks"
date: 2009-02-25
forum: General Help
---

### Post by harivittal.hk on 2009-02-25
hi!friends m not able to mount any of my harddisk drives its asking for authentication everytime......so m not able to open them n view the contents

---

### Post by RedSingularity on 2009-02-25
Just enter your password that you use to login to Ubuntu.

---

### Post by harivittal.hk on 2009-02-25
hey i gave in tat way only.......but still its not opening

---

### Post by taurus on 2009-02-25
Which harddrives are you trying to mount?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by harivittal.hk on 2009-02-25
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x215e215d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   b  W95 FAT32
/dev/sda6            7649       12110    35840983+   7  HPFS/NTFS
/dev/sda7           12111       16572    35840983+   7  HPFS/NTFS
/dev/sda8           16573       19456    23165698+  83  Linux

---

### Post by harivittal.hk on 2009-02-25
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              22G  5.0G   16G  25% /
tmpfs                 247M     0  247M   0% /lib/init/rw
varrun                247M  100K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M  2.7M  244M   2% /dev
tmpfs                 247M  244K  247M   1% /dev/shm
lrm                   247M  2.0M  245M   1% /lib/modules/2.6.27-7-generic/volatile

---

### Post by taurus on 2009-02-25
So you want to mount /dev/sda1, /dev/sda5, /dev/sda6, & /dev/sda7!

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following lines to the end of it.

```

/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda6   /media/sda6   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda7   /media/sda7   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000  0  0

```
Save it and close down gedit editing window.  Then, create those new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7
sudo mount -a
df -h
```

Assuming you are in the US, **en_US**.

---

