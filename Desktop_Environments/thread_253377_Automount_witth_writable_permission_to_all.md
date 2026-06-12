---
title: "Automount witth writable permission to all?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by JeffBlouin on 2006-09-08
Hi,

  Here is my problem:  I Have a 200Gig external USB Hardrive in vfat32 I can read and copy things to the Harddrive but cannot delete files without being in sudo mode. 

The other problem i have is when i try to save a file from a downloading sofware like bittorent or DC++ on the USB hard drive, it doesn't work. I thing i need to give permission to all user to this drive but don't know how?

It's not showing up in fstab... but it automount and show up on mu desktop  

Thanks alot
Jeff

---

### Post by Azathoth_ on 2006-09-08
You have to change fstab in the parameters of ro changing por rw and changing guid=    for other values.
My fstab is the next if you want to compare:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,iocharset=utf8,codepage=850,utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,iocharset=utf8,codepage=850,utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,iocharset=utf8,codepage=850,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     vfat    defaults,iocharset=utf8,codepage=850,utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by JeffBlouin on 2006-09-09
Thanks for the reply but it doesn't work...,

When I make a entry in fstab like the one you have with my usb device,the usb drive appear on the desktop but i cannot acces anything in it + there is ne write permission for the users...

Anything else i could try?

Thanks

---

