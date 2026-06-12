---
title: "New CD-Rom won't mount"
date: 2008-06-06
forum: Desktop Environments
---

### Post by boralyl on 2008-06-06
I just put in a new CD/DVD combo drive and I can't get it to mount.  
"lshw -C disk" gives me:
```

*-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0007/04/05 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2

```

And my current /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18af3d57-4f93-4d8d-aa73-ae713cb67524 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7b82a85e-0a1d-48fa-87b6-85dfaec2ea40 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /media/Albums   ntfs-3g defaults,locale=en_US.utf8 0 0

```

When I try to mount i manually I receive an error as shown below:
```

sudo mount -t iso9660 /dev/cdrom2 /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I also tried the logical name /dev/sr0 but get the same results.  Any suggestions on how to resolve this?

---

### Post by boralyl on 2008-06-06
I tentatively got it to work.  I can run the command 
```

sudo mount -t iso9660 /dev/cdrom2 /media/cdrom0

```

and it atleast mounted, where as 

```

sudo mount -t iso9660 /dev/cdrom2 /media/cdrom

```

failed.  FYI /media/cdrom is just a symlink to /media/cdrom0.  So I gave it the direct path and it mounted fine, in case anyone else experineces this issue.  I will try to reboot then and change /dev/sr0 to /dev/cdrom2 to see if it automounts.  I was confused because so many logical names were listed on the output of lshw

---

