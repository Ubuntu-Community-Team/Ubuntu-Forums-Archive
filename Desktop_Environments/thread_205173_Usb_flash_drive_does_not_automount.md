---
title: "Usb flash drive does not automount"
date: 2006-06-28
forum: Desktop Environments
---

### Post by nedkelly on 2006-06-28
I have got a strange problem with my usb stick. I can not get it to auto mount in drapper. It worked in Breezy and works in Windows XP.

And I have checked System-->Preferences-->Removabel drives and media and all options is checked.

I get this from my dmesg

```
[17182566.436000] ohci_hcd 0000:00:02.0: wakeup
[17182566.820000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[17182567.048000] scsi1 : SCSI emulation for USB Mass Storage devices
[17182567.048000] usb-storage: device found at 3
[17182567.048000] usb-storage: waiting for device to settle before scanning
[17182572.228000] usb 1-2: reset full speed USB device using ohci_hcd and address 3
[17182572.616000] usb 1-2: reset full speed USB device using ohci_hcd and address 3
[17182573.004000] usb 1-2: reset full speed USB device using ohci_hcd and address 3
[17182573.212000] usb-storage: device scan complete

```

---

### Post by jazzgossen on 2006-06-28
Is there nothing about sd* there, such as sda, sdb, sdc, sda1? Does "ls /dev/sd*" give anything?

---

### Post by aysiu on 2006-06-28
Can you plug the USB stick in and then post here the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by nedkelly on 2006-06-28
#2 no there are no sda, sdb and so on  devices

#3 the information from the commands you wanted

**sudo fdisk -l**
```

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         974     7823623+   7  HPFS/NTFS
/dev/hda2             975        2798    14651280   83  Linux
/dev/hda3            2799        2859      489982+  82  Linux swap / Solaris
/dev/hda4            2860        9732    55207372+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/hdb2            2434       20772   147308017+  83  Linux
/dev/hdb3           20773       24321    28507342+  83  Linux

```

**df -h**

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G  8.8G  5.3G  63% /
varrun                252M  124K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  132K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-25-386/volatile
/dev/hda1             7.5G  7.2G  326M  96% /media/hda1
/dev/hda4              53G   42G   11G  80% /media/hda4
/dev/hdb1              19G   13G  5.9G  69% /media/e-drev
/dev/hdb2             141G   74G   68G  53% /media/hdb2
/dev/hdb3              27G   23G  3.4G  87% /media/f-drev

```

**cat /etc/fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>                              <dump>  <pass>
proc            /proc           proc     defaults                                 0       0
/dev/hda2       /               reiserfs notail                                   0       1
/dev/hda1       /media/hda1     ntfs     defaults,nls=utf8,umask=007,gid=46       0       1
/dev/hda4       /media/hda4     vfat     defaults,utf8,umask=000                  0       0
/dev/hda3       none            swap     sw                                       0       0
/dev/hdb1       /media/e-drev   vfat     defaults,utf8,umask=000                  0       0
/dev/hdb2       /media/hdb2     reiserfs defaults
/dev/hdb3       /media/f-drev   ext2     defaults                                 0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                           0       0

```

---

### Post by aysiu on 2006-06-28
Yeah, it looks as if you have a problem more fundamental than the drive not *mounting*. It doesn't even appear to exist--mounted or unmounted.

Maybe it's a hardware connection problem--the USB port being a little jiggled out of place?

---

### Post by nedkelly on 2006-06-29
no it works in Windows XP on the same port, and it worked in Breezy on the same port. 
Somebody got any idea??

---

### Post by maxym.hryniv on 2008-01-06
I have exactly the same problem. Anybody knows how to solve?

---

### Post by zorkerz on 2008-01-16
Im running hardy so this may be the wrong place but I also have the same problem. If I restart the computer it mounts fine its only when I plug it in with ubuntu already running.

---

### Post by allforcarrie on 2008-01-17
thats weird.

---

### Post by maxym.hryniv on 2008-01-17
Btw it's ok in winXP and was ok in PClinuxOS and Mandriva.

---

### Post by rowtc2 on 2008-01-17
Give a restart without the flash and then enter the usb. If doesn't work give a restart with usb in. But wait 1 min before appear the new mount.

---

