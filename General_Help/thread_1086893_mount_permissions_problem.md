---
title: "mount permissions problem"
date: 2009-03-04
forum: General Help
---

### Post by chriskin on 2009-03-04
it seems that i no longer have the permissions to mount external drives, meaning that i can either have my external drive pluged in before login to recognise it or i can not have it recognised at all. also , i can not mount usb drives that have not been mounted before.

can someone help me obtain full mount permissions?

:popcorn:

---

### Post by albandy on 2009-03-04
type "groups" in the console and paste it here

---

### Post by chriskin on 2009-03-04
here you are :

christos root adm dialout fax cdrom tape audio dip video plugdev scanner fuse lpadmin netdev sambashare debian-tor kvm sudo admin vboxusers

:)

---

### Post by taurus on 2009-03-04
With an external drive plugged in, post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```

---

### Post by chriskin on 2009-03-04
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281440+  a5  FreeBSD
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       19202    45263137+  83  Linux
/dev/sda4           19203       19457     2048287+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005bff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


sdb is the external drive
do you want me to post what comes when a usb is on?

---

### Post by chriskin on 2009-03-04
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              43G   22G   19G  54% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  376K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M   12K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             233G  176G   58G  76% /media/disk
/dev/sda2              93G   50G   44G  54% /media/windows

---

### Post by taurus on 2009-03-04
What happens if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by albandy on 2009-03-04
your're in the group plugdev so you should be able to mount usb volumes.

go to System--> Administration --> Authorizations
search for storage, then go to "mount filesystems from removable drives"
and add your user

---

### Post by chriskin on 2009-03-04
> **albandy said:**
> your're in the group plugdev so you should be able to mount usb volumes.

go to System--> Administration --> Authorizations
search for storage, then go to "mount filesystems from removable drives"
and add your user


do i have to reboot to see the changes working?

edit :  even after restart , it doesn't mount

> **taurus said:**
> What happens if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

it worked finely with those commands , thank you
it showed these lines after the df -h command

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              43G   22G   19G  54% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  360K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M   12K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda2              93G   50G   44G  54% /media/windows
/dev/sdb1             233G  176G   58G  76% /media/sdb1


yet i get a message saying  "cannot unmount, volume is not mounted" is i try to unmount it

---

### Post by taurus on 2009-03-04
```
sudo umount /dev/sdb1
df -h
```

---

### Post by chriskin on 2009-03-04
both work , is there any way to make it mount this way just by clicking on it?

---

