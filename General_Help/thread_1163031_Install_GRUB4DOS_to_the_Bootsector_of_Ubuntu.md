---
title: "Install GRUB4DOS to the Bootsector of Ubuntu?"
date: 2009-05-18
forum: General Help
---

### Post by Panarchy on 2009-05-18
Hello

Is it possible to install GRUB4DOS into the bootsector of Ubuntu?

I've been able to successfully download, extract, compile & install the latest GRUB4DOS, however I can't work out how to load it into the BootSector.

Any ideas?

Thanks in advance,

Panarchy

BTW: Ubuntu 8.10 64-bit

EDIT: Does this guide look correct? [http://diddy.boot-land.net/grub4dos/files/install_linux.htm](http://diddy.boot-land.net/grub4dos/files/install_linux.htm)

---

### Post by bacardiandwatermelon on 2009-05-18
What's the benefit to using grub4dos over grub?

---

### Post by ikonia on 2009-05-19
the boot sector is nothing to do with the operating system - it's on the MBR of the disk.

You can install what ever you want onto the boot sector of the disk

This has been covered in your many discussions on irc

---

### Post by VMC on 2009-05-19
> **Panarchy said:**
> Hello

Is it possible to install GRUB4DOS into the bootsector of Ubuntu?

I've been able to successfully download, extract, compile & install the latest GRUB4DOS, however I can't work out how to load it into the BootSector.
...
EDIT: Does this guide look correct? [http://diddy.boot-land.net/grub4dos/files/install_linux.htm](http://diddy.boot-land.net/grub4dos/files/install_linux.htm)
Maybe give us a reason as to why you want to use grub4dos instead of grub legacy?

I've had to use grub4dos on one of my laptops because of issues with cdrom. I don't have it in front of me, but I got it to work.

To answer the link question, yes that looks correct.

---

### Post by Panarchy on 2009-05-21
Okay VMC, thanks.

bacardiandwatermelon: For booting the Windows BootLoader

---

### Post by Panarchy on 2009-05-21
Unfortunately, I am as yet unable to get this to work.

```
sudo /boot/Grub4DOS/stage2/bootlace.com /dev/sdb7

Error: Invalid partition table. Must specify --floppy explicitly for floppy.

BOOTLACE writes GRLDR BOOT RECORD to MBR or to the boot area of a file system.
Usage:  bootlace.com  [OPTIONS]  DEVICE_OR_FILE
Options: --read-only, --floppy[=N], --boot-prevmbr-first, --boot-prevmbr-last,
--no-backup-mbr, --force-backup-mbr, --mbr-enable-floppy, --mbr-disable-floppy,
--mbr-enable-osbr, --mbr-disable-osbr, --duce, --time-out=T, --hot-key=K, 
--preferred-drive=D, --preferred-partition=P, --sectors-per-track=S, --heads=H,
--start-sector=B, --total-sectors=C, --install-partition=I, --lba, --chs,
--fat12, --fat16, --fat32, --vfat, --ntfs, --ext2, --serial-number=SN,
--restore-mbr, --mbr-no-bpb, --chs-no-tune
DEVICE_OR_FILE: Filename of the device or image. For DOS, a BIOS drive number
(in hex 0xHH or decimal DDD format)can be used to access the drive.
```

Please help me out.

Thanks in advance,

Panarchy

---

### Post by dandnsmith on 2009-05-21
According to that guide (link posted by OP), the line should be:

```
sudo /boot/Grub4DOS/stage2/bootlace.com --floppy=7 /dev/sdb7
```

as I read it.

---

### Post by ikonia on 2009-05-21
Grub can boot the windows boot loader - there is no reason to use grub4dos here.

---

