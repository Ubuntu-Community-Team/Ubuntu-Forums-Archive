---
title: "No automount"
date: 2005-11-21
forum: Desktop Environments
---

### Post by art on 2005-11-21
Hi forum
I hope someone can help... I have an external HDD, partitioned as FAT32 + NTFS. Now when I plug it in, only NTFS partition gets mounted, and VFAT no. I can mount it manually, but I would certainly prefer it to mount automaticaly. This is my fdisk -l relevant piece

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3160    25382668+   c  W95 FAT32 (LBA)
/dev/sda2            3161        9729    52765461    7  HPFS/NTFS

and this is my mount -l

/dev/hda2 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-686/volatile type tmpfs (rw,mode=0755)
/dev/hda5 on /home type ext3 (rw,user_xattr) [/home]
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/NTFS type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

### Post by aysiu on 2005-11-21
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by kruz on 2005-11-21
check it, if your lazy and not wana go do it 
lol


worked for me?

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

/dev/sda1      /media/windows  vfat    iocharset=utf8,umask=000   0       0

i actually make mine something like this

sudo mkdir ~/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab


/dev/sda1      ~/windows  vfat    iocharset=utf8,umask=000   0       0

~/=your home dir

/home/(username)
so its easier for me to acess
cheers!

---

### Post by art on 2005-11-21
Thanks aysiu, but the problem is (I forgot to mention) that this is an external USB drive, ie when I plug it in, it gets a /dev/sda1, and I think if I plug it in after something else has been plugged in, it will get a different name, so I can't quite put it in fstab, right?

---

### Post by kruz on 2005-11-21
add that line in there that i gave u +
like 4 lines like it but with different numbers
sda1 , 2 ,3 ,4 etc

so whatever its on, it gets mountded

so if 1 3 4 dont exists itll just fail to mount
and mount 2
thats my theory at least
let me look into a "startup script"

cuz gnome has a feature like
command on USB plugin or w/e

---

### Post by aysiu on 2005-11-21
Can you verify that actually happens?
Plug it in? Type ```
sudo fdisk -l
``` Unplug it.
Plug something else in. Unplug it. 
Plug it in again. Type ```
sudo fdisk -l
```

See if you get /dev/sda1 all the time or if it actually varies.

Frankly, something's wrong. If it's an external drive, it should automount. You may want to consider filing a bug report. I know Breezy has had some automount issues in both Gnome and KDE.

---

### Post by art on 2005-11-21
So here it goes:
I mount a USB jump drive (FAT16) -> sudo fdisk -l

/dev/sda1   *           1         246      507375+   4  FAT16 <32M

I plug in the USB HDD (FAT32+NTFS) (through a USB hub)-> sudo fdisk -l

/dev/sda1               1        3160    25382668+   c  W95 FAT32 (LBA)
/dev/sda2            3161        9729    52765461    7  HPFS/NTFS

but only sda2 is in /etc/mtab. So I guess as kruz suggested i could put it in fstab, but i think this is not the way it should be.

---

### Post by art on 2005-11-21
Does the first partition need to be set Active, if it is not bootable?

---

### Post by aysiu on 2005-11-21
The USB drive is partitioned? I wonder if that's what makes the difference.
Perhaps it doesn't know what filesystem to mount it as.

---

### Post by art on 2005-11-21
[QUOTE=aysiu]The USB drive is partitioned? I wonder if that's what makes the difference.
Perhaps it doesn't know what filesystem to mount it as.[/QUOTE]

sudo fdisk -l 

/dev/sda1 1 3160 25382668+ c W95 **FAT32** (LBA)
/dev/sda2 3161 9729 52765461 7 HPFS/NTFS

The drive is partitioned, with Partition Magick. The Bolded is what the OS think the partition is, isn't it. So it seems that Ubuntu sees it as FAT32, no?

---

### Post by art on 2005-11-21
[QUOTE=art]sudo fdisk -l 

/dev/sda1 1 3160 25382668**_+ c_** W95 FAT32 (LBA)
/dev/sda2 3161 9729 52765461 7 HPFS/NTFS

I just noticed, what's the bolded region here supposed to mean?

---

### Post by aysiu on 2005-11-21
I don't know what it means, but I have that + sign in mine, too: ```
 sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3           18495       19457     7735297+  83  Linux
/dev/hda5            1912       14763   103233658+   b  W95 FAT32
/dev/hda6   *       14764       16434    13422276   83  Linux
/dev/hda7           18363       18494     1060258+  82  Linux swap / Solaris
/dev/hda8           16435       18362    15486628+  83  Linux

Partition table entries are not in disk order
``` So, are you saying it always mounts at /dev/sda1 and always as FAT32? If so, I'd go ahead and put it in the /etc/fstab.

---

### Post by art on 2005-11-21
Yeah, I guess that's the easiest solution...
Well, thanks a lot for help aysiu and kruz!

---

### Post by aysiu on 2005-11-21
[QUOTE=art]Yeah, I guess that's the easiest solution...
Well, thanks a lot for help aysiu and kruz![/QUOTE] Does that mean it worked?

---

### Post by kruz on 2005-11-21
[QUOTE=art]Yeah, I guess that's the easiest solution...
Well, thanks a lot for help aysiu and kruz![/QUOTE]


ill try to insert more info on that auto script later ima do some testing

---

### Post by art on 2005-11-22
Well, I noticed that in aysiu's fdisk the ID for FAT32 is "b", mine was a "c", so I changed that with sfdisk, but still, the same problem. And putting it into fstab, it doesn't automount, only when I fo mount -a it does...

---

### Post by art on 2005-11-22
Well, I'm pretty much out of ideas... Any ideas out there? Does this sound like a bug, which needs to filed, or...

---

### Post by aysiu on 2005-11-22
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

### Post by art on 2005-11-22
hope it gets fixed...

---

### Post by beeyarkay on 2005-11-28
I do have the same problem. My scenario is that I have a dual boot machine(laptop) WinXP and Ubuntu 5.10

I have 3 drives on Windows C/D/E. E is a FAT32 partition. All these have been added to /etc/fstab. During startup, both my NTFS partitions (C&D) get mounted. E, which is the FAT32 partition does not mount. Although, I can mount it manually. I use the command <<mount /media/edrive>>. /media/edrive is the folder where my edrive mounts according to the configuration in /etc/fstab

If someone has fixed this issue, please help.....

Thanks,
Ramesh

---

