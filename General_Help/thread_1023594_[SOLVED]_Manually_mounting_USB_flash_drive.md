---
title: "[SOLVED] Manually mounting USB flash drive"
date: 2008-12-28
forum: General Help
---

### Post by Nicholas Escalona on 2008-12-28
Linux noob here. I'm trying to manually mount my USB drive while running Arch Linux on LiveCD. What follows is the *new* output I get from [FONT="Courier New"]lsusb[/FONT] when drive is inserted.

```

Bus 002 Device 007: ID 05dc:a430 Lexar Media, Inc.

```

So the drive is recognized. It seems to be located at [FONT="Courier New"]/dev/sdf[/FONT], with the lone partition at [FONT="Courier New"]/dev/sdf1[/FONT]. The drive is consistently assigned here. I said [FONT="Courier New"]ls /dev | grep -i "sd"[/FONT] twice to get the difference.

So, how can I mount the drive? I'd like to mount it to [FONT="Courier New"]/mnt/usbflash[/FONT], which I've already created.

---

### Post by jerome1232 on 2008-12-28
```
mkdir /mnt/usbflash
mount /dev/sdf1 /mnt/usbflash
```

You will probably need to be root to do this.

To unmount it (always unmount before you remove the flashdrive from it's port)
```
umount /mnt/usbflash
```

---

### Post by Nicholas Escalona on 2008-12-28
```
[root@archlive ~]# mkdir /mnt/usbflash
[root@archlive ~]# mount /dev/sdf1 /mnt/usbflash
mount: you must specify the filesystem type
[root@archlive ~]# mount -t auto /dev/sdf1 /mnt/usbflash
mount: you must specify the filesystem type
[root@archlive ~]# mount -t usbfs /dev/sdf1 /mnt/usbflash
[root@archlive ~]# ls /mnt/usbflash
001  002  003  004  005  devices
```

I know these are not the correct contents of the drive.

---

### Post by procras on 2008-12-28
> **Nicholas Escalona said:**
> ```

[root@archlive ~]# mkdir /mnt/usbflash
[root@archlive ~]# mount /dev/sdf1 /mnt/usbflash
mount: you must specify the filesystem type
[root@archlive ~]# mount -t auto /dev/sdf1 /mnt/usbflash
mount: you must specify the filesystem type
[root@archlive ~]# mount -t usbfs /dev/sdf1 /mnt/usbflash
[root@archlive ~]# ls /mnt/usbflash
001  002  003  004  005  devices
```

I know these are not the correct contents of the drive.

Most usb pens are formatted in fat32 or some such. 
You can check the type it is formatted to using gparted or fdisk

Also I would suggest looking at the messages in syslog when you plug in the pen etc. Open a terminal and try tail -f /var/log/syslog

---

### Post by vanadium on 2008-12-28
The mount command should be able to recognize the file system type. THat it does not might indicate problems with the partition table and/or file system on the USB.

To make sure how your USB is seen, use the command "sudo fdisk -l" (with the USB inserted). You can indeed try mounting specifying "vfat" or "msdos" as file systems.

---

### Post by Nicholas Escalona on 2008-12-28
Thanks all, I resolved the problem. The drive was actually appearing under [FONT="Courier New"]/dev/sdb[/FONT], so I mounted [FONT="Courier New"]/dev/sdb1[/FONT] and guessed VFAT and it worked.

---

