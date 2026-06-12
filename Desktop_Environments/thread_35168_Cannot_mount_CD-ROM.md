---
title: "Cannot mount CD-ROM"
date: 2005-05-17
forum: Desktop Environments
---

### Post by dmly on 2005-05-17
Hi,
I have Ubuntu 5.04 and it is running fine. Until yesterday I find out a problem with mouting CDROM (an Audio cd). 

When I insert a CD-ROM, look like it gets automount. Because I see the cdrom icon on the desktop. When i open the icon, it did open up the browser to see files in the cdrom.
Oddly, in the /media/cdrom0, there is nothing mounted there.
I manually mounted the cdrom and get this error:

$ mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /boot           ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /mnt/usb        vfat    rw,user,noauto  0       0
/dev/hda1       /mnt/ntfs       ntfs    defaults,user,exec,umask=000,utf8       
0       0

Here is my dmesg message
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1024
UDF-fs: No partition found (1)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

It is really annoying when you can browser the CDrom but cannot play music or do anything with it.

Thank you for helping.
Doug

---

### Post by Xian on 2005-05-17
[QUOTE=dmly]Oddly, in the /media/cdrom0, there is nothing mounted there.
I manually mounted the cdrom and get this error:

$ mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/hdc,

Here is my fstab

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0[/QUOTE]

Try this:

```
$ sudo mount /media/cdrom0
```

---

### Post by dmly on 2005-05-17
Uh uh.. not working either. Same error message

---

### Post by wwwolf on 2005-05-18
[QUOTE=dmly]Uh uh.. not working either. Same error message[/QUOTE]

How about:

sudo mount /dev/hdc

---

### Post by reedlaw on 2005-05-31
I get the same error.

---

