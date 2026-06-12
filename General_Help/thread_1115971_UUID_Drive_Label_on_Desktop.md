---
title: "UUID Drive Label on Desktop"
date: 2009-04-04
forum: General Help
---

### Post by gotmonkey on 2009-04-04
I am running Ubuntu 8.10 as a file server on my home network with multiple drives. 

1x250GB for the OS and Swap. /dev/sdc
1x1TB (RAID 10 / 4x500GB on 3Ware 9650SE as storage
1x500GB as a transfer/processing drive

Initially, the 

When I boot system, the storage drive and the transfer drive seem to change their device boot designation in fdisk -l

I pulled the drive info "#sudo vol_id /dev/sdx1"

ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=ef983a41-bcb0-4e34-aceb-a89455d5aaf3
ID_FS_UUID_ENC=ef983a41-bcb0-4e34-aceb-a89455d5aaf3
ID_FS_LABEL=transfer
ID_FS_LABEL_ENC=transfer
ID_FS_LABEL_SAFE=transfer

I switched the transfer drive to UUID in the fstab so it reads: 
UUID:xxxxxxxx /mount/point auto 0 1

The drive mounts just fine, but when it does the short cut on the desktop names it as "500.1 GB Media". When I had the drive listed in the fstab as "/dev/sdx1 /mount/point auto 0 1", the shortcut on the desktop showed as "transfer"

Anyone know how to set the drive up so the shortcut lists as the drives label that is listed in the ID_FS_LABEL?

Thanks

---

### Post by cariboo on 2009-04-04
Use  gparted to create a disk label for you hard drive, then the disk label wiil show when the drive is mounted.

JIm

---

### Post by fjgaude on 2009-04-04
I believe all you do is this:

LABEL=transfer /mount/point auto 0 0

---

### Post by gotmonkey on 2009-04-04
> **cariboo907 said:**
> Use  gparted to create a disk label for you hard drive, then the disk label wiil show when the drive is mounted.

JIm

I created the drive under gparted and set the label. I think that it has something to do with the fstab and UUID

---

### Post by gotmonkey on 2009-04-04
> **fjgaude said:**
> I believe all you do is this:

LABEL=transfer /mount/point auto 0 0

I tried putting that into the fstab and it through up an error when I mounted the drive.

---

### Post by fjgaude on 2009-04-05
Strange, are you sure the LABEL is "transfer"? The drive didn't mount automatically?

---

### Post by gotmonkey on 2009-04-07
> **fjgaude said:**
> Strange, are you sure the LABEL is "transfer"? The drive didn't mount automatically?

maybe I formatted incorrectly

UUID:xxxxxxxxxxx LABEL= transfer /media/transfer ext3 auto,rw 0 1

---

### Post by mcduck on 2009-04-07
> **gotmonkey said:**
> maybe I formatted incorrectly

UUID:xxxxxxxxxxx LABEL= transfer /media/transfer ext3 auto,rw 0 1

you can either use the UUID, or the label, to specify which drive to mount. Not both.

To change the name the drive gets when mounted you need to change the mount point (and of course make sure the mount point you define in fstab also exists).

So, in this case first make sure that you have a directory /media/transfer. Then you can define your drive in fstab like this:
```

UUID=xxxxxxxxxx /media/transfer ext3 auto,rw 0 2
```
or like this:
```

LABEL=transfer /media/transfer ext3 auto,rw 0 2
```

I changed the last number to "2" as "1" should only be used for root partition, for all others it's either "2" (to run fsck on that partition after root has been checked), or "0" (to not check the partition at all).

---

