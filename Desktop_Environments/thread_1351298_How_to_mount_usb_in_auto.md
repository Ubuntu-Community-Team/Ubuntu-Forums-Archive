---
title: "How to mount usb in auto?"
date: 2009-12-10
forum: Desktop Environments
---

### Post by isterios on 2009-12-10
Hello,

I have an external usb drive attached to my laptop.

I would like it to be mounted each time I start my xubuntu.

Actually, I have to double click on it or to right click/mount.

Is there an easy solution?

Tks

---

### Post by emigrant on 2009-12-10
please past the output for the following:

```
sudo ls -l /dev/disk/by-uuid/

```

```
sudo fdisk -l
```


```
gedit /etc/fstab
```

---

### Post by isterios on 2009-12-10
> **emigrant said:**
> please past the output for the following:

```
sudo ls -l /dev/disk/by-uuid/

```

lrwxrwxrwx 1 root root 10 2009-12-10 19:01 5f18b7fc-e798-40e2-b8d2-4a2b3f32eb32 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-12-10 19:01 e3ee3997-7657-4658-b2cc-4bd614316a7b -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-12-10 19:02 edb8ce74-5dd3-4d66-a9e8-657d0f9d420a -> ../../sdb1

```
sudo fdisk -l
```
(I just past the line linked to my external disk)
/dev/sdb1               1       38913   312568641    b  W95 FAT32


```
gedit /etc/fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5f18b7fc-e798-40e2-b8d2-4a2b3f32eb32 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=e3ee3997-7657-4658-b2cc-4bd614316a7b none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by emigrant on 2009-12-10
please do the following:

```
sudo umount -a
```//unmount all drives

```
sudo cd /media/
```//go to the director /media

```
sudo mkdir drive_usb
```//create a new directory (mount point for the usb drive)

```
sudo gedit /etc/fstab
```//open fstab with super user rights

add this to the end of fstab:

```
UUID=edb8ce74-5dd3-4d66-a9e8-657d0f9d420a /media/drive_usb vfat auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

```
sudo mount -a
```
// mount all drives

---

### Post by isterios on 2009-12-10
Thank you Emigrant.

I see you mount using fstab.

So you confirm there is no specific option in xubuntu to automount these usb devices (when they are already plugued?)

---

### Post by emigrant on 2009-12-10
here after you don't want to do anything. each time you restart the drive will be auto mounted :).
did you check restarting?

---

### Post by isterios on 2009-12-10
No I have not tested yet, but I am sure your config. works ;)

I just wondered if there was an "already made" solution included in xubuntu.

---

### Post by emigrant on 2009-12-11
> **isterios said:**
> No I have not tested yet, but I am sure your config. works ;)

I just wondered if there was an "already made" solution included in xubuntu.
already made solutions are not available for the above problem in all *buntus as far as i know :)

---

### Post by isterios on 2009-12-14
Thanks Emigrant for ur help ;)

---

### Post by aspiredfang on 2009-12-14
There's a nice little mount manager called pysdm that features a GUI. once set up it will automatically mount any drives you have configured it for.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

It's available from within the *buntu repositories also :)

---

### Post by isterios on 2009-12-19
Tks

---

### Post by gordon3913 on 2009-12-20
I am having trouble trying to mount any usb device in Ubuntu 9.10
I followed your steps above and still got this error message

gordon@gordon-desktop:/media$ sudo mount -a
mount: special device UUID=edb8ce74-5dd3-4d66-a9e8-657d0f9d420a does not exist
gordon@gordon-desktop:/media$ 

Hear is the message in /var/log/messages

Dec 21 10:39:56 gordon-desktop kernel: [ 8137.786975] usb 1-3: configuration #1 chosen from 1 choice
Dec 21 10:39:56 gordon-desktop kernel: [ 8137.795942] scsi8 : SCSI emulation for USB Mass Storage devices
Dec 21 10:40:01 gordon-desktop kernel: [ 8142.799486] scsi 8:0:0:0: Direct-Access     Zipp     4GB              8.07 PQ: 0 ANSI: 2
Dec 21 10:40:01 gordon-desktop kernel: [ 8142.833672] sd 8:0:0:0: Attached scsi generic sg6 type 0
Dec 21 10:40:01 gordon-desktop kernel: [ 8142.846838] sd 8:0:0:0: [sde] 7864320 512-byte logical blocks: (4.02 GB/3.75 GiB)
Dec 21 10:40:01 gordon-desktop kernel: [ 8142.856283] sd 8:0:0:0: [sde] Write Protect is off
Dec 21 10:40:01 gordon-desktop kernel: [ 8142.873857]  sde: sde1
Dec 21 10:40:01 gordon-desktop kernel: [ 8143.020388] sd 8:0:0:0: [sde] Attached SCSI removable disk
Dec 21 10:40:47 gordon-desktop kernel: [ 8189.305840] usb 1-3: USB disconnect, address 7
Dec 21 10:40:50 gordon-desktop kernel: [ 8192.324156] usb 1-4: new high speed USB device using ehci_hcd and address 8
Dec 21 10:40:51 gordon-desktop kernel: [ 8192.591550] usb 1-4: configuration #1 chosen from 1 choice
Dec 21 10:40:51 gordon-desktop kernel: [ 8192.604432] scsi9 : SCSI emulation for USB Mass Storage devices
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.605908] scsi 9:0:0:0: Direct-Access     Zipp     4GB              8.07 PQ: 0 ANSI: 2
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.638659] sd 9:0:0:0: Attached scsi generic sg6 type 0
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.647539] sd 9:0:0:0: [sde] 7864320 512-byte logical blocks: (4.02 GB/3.75 GiB)
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.654483] sd 9:0:0:0: [sde] Write Protect is off
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.680243]  sde: sde1
Dec 21 10:40:56 gordon-desktop kernel: [ 8197.790923] sd 9:0:0:0: [sde] Attached SCSI removable disk

---

### Post by sameerds on 2009-12-22
> **emigrant said:**
> here after you don't want to do anything. each time you restart the drive will be auto mounted :).
did you check restarting?

I think "auto mount at restart" is not the problem that the original poster is trying to address. While the system is powered on, whenever the external drive is connected, it should be mounted automatically. This cannot be done through fstab, and in fact I am looking for the answer too!

---

