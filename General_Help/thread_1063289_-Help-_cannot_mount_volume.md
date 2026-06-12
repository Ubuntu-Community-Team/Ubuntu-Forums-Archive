---
title: "-Help- cannot mount volume"
date: 2009-02-07
forum: General Help
---

### Post by jadin on 2009-02-07
in ubuntu, when i go to [places>computer] and try to go into another one of my drives i get the "cannot mount volume" error messege. please help!

i installed ntfs-3g
and this is my sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35ef35ee

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8679c0c

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 16573 133122591 7 HPFS/NTFS
/dev/sdb2 16574 30400 111065377+ f W95 Ext'd (LBA)
/dev/sdb5 16574 30400 111065346 7 HPFS/NTFS

please help me

---

### Post by taurus on 2009-02-07
Are you trying to mount both /dev/sdb1 & /dev/sdb5?

```
sudo mkdir /media/sdb1 /media/sdb5
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
sudo mount -t ntfs-3g /dev/sdb5 /media/sdb5
df -h
```

---

### Post by jadin on 2009-02-07
when i start with 
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
it's writing me:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g force 0 0

---

### Post by jadin on 2009-02-07
what do u think taurus? 
please try help me :)

---

### Post by taurus on 2009-02-07
Looks like the last time you used windows, you didn't shut it down cleanly.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
sudo mount -t ntfs-3g /dev/sdb5 /media/sdb5
df -h
```

---

### Post by jadin on 2009-02-07
i don't have windows..

---

### Post by jadin on 2009-02-07
yeah i used..
sec i'll try what u gave me..

---

### Post by jadin on 2009-02-07
oh man u did it :))

u helped me and saved me time!
thx!!! keep it pure :))

---

