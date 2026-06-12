---
title: "Mount my SD card writable"
date: 2007-01-18
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2007-01-18
Hi,

I use Ubuntu Edgy.

I have a SD card reader integrated in my laptop. I followed the procedure described at [ThinkWiki]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working#Ubuntu_6.10_.27edgy_eft.27:") so the card is auto mounted when inserted.

But it is mounted as readable only. So I unmounted the device and tried to mount it writable:

```
/media$ sudo mount /dev/mmcblk0p1 mmcdisk/ -rw
mount: block device /dev/mmcblk0p1 is write-protected but explicit `-w' flag given
```

And the card is not mounted.

However, I know it is ***not*** write-protected because my camera can write photos on it!

So, how am I supposed to make this card writable with Ubuntu?

Thanks!

---

### Post by taurus on 2007-01-18
```
sudo mount -t vfat  /dev/mmcblk0p1  /media/mmcdisk  -o  iocharset=utf8,umask=000
```

---

### Post by Jonathan Métillon on 2007-01-18
Thank you Taurus ! But...

```
/media$ sudo mount -t vfat  /dev/mmcblk0p1  /media/mmcdisk  -o  iocharset=utf8,umask=000
mount: block device /dev/mmcblk0p1 is write-protected, mounting read-only
```

---

### Post by taurus on 2007-01-18
And you think it's vfat/fat32!  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Jonathan Métillon on 2007-01-18
The output is: 

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9331    74951226   83  Linux
/dev/hda2            9332        9729     3196935    5  Extended
/dev/hda5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/mmcblk0: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         965      246989+   6  FAT16
```So it Windows formated and that's why I can't write on it? Why a camera would use a Windows partition? Isn't there some ISO kind of universal filesystem for memory card? Sorry for my newbiness man :-)

---

### Post by taurus on 2007-01-18
```

sudo umount  /dev/mmcblk0p1
sudo mount  -t  vfat  /dev/mmcblk0p1  /media/mmcdisk  -o  iocharset=utf8,umask=000
mount

```

---

### Post by Jonathan Métillon on 2007-01-19
I didn't see the difference with the last command? :confused:

This resulted again in: 

```
/media$ sudo umount  /dev/mmcblk0p1
/media$ sudo mount  -t  vfat  /dev/mmcblk0p1  /media/mmcdisk  -o  iocharset=utf8,umask=000
mount: block device /dev/mmcblk0p1 is write-protected, mounting read-only
```

Then the mount command outputed:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda on /media/usbdisk type ext3 (rw,nosuid,nodev)
/dev/mmcblk0p1 on /media/mmcdisk type vfat (ro,iocharset=utf8,umask=000)
```

Thanks for your time Taurus!

---

### Post by ianw1974 on 2007-02-28
This might work for you:

```
mkdir /media/sdcard
chmod u+w /media/sdcard
```

then edit /etc/fstab, and add the following:

```
/dev/mmcblk0p1  /media/sdcard   auto    umask=0,rw,user,auto    0       0
```

that's what I've just done on mine.  And it's working a treat now.

---

### Post by alekkova on 2007-09-23
Remount SD card  with rv options.


mkdir /media/sdcard
chmod u+w /media/sdcard

then edit /etc/fstab, and add the following:

/dev/mmcblk0p1 /media/sdcard auto umask=0,rw,user,auto 0 0

mount -o remount -o rv /dev/mmcblk0p1 



That's what I've just done and it's working.

---

