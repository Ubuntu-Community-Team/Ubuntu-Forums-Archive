---
title: "CD mount issues on Inspiron 3700 with Feisty"
date: 2007-06-26
forum: Dell  Ubuntu Support
---

### Post by FatFreddy on 2007-06-26
Hi guys,

First post so be kind....

I loaded Feisty last week but cannot get the CD to recognize a disc.  When I go to Places/ Computer I can see the CD and HD, but when I click on the CD (with a valid CD in drive) I get a message "Unable to mount media.  There is probably no Media in the drive."

Any ideas?

user@user-laptop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6560a613-c936-4d9a-b7ff-b073edb5559e /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=d72c11c3-fed4-4a89-8028-1c866acfcc66 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

user@user-laptop:~$ dmesg | grep cd
[26746.290835] uhci_hcd 0000:00:07.2: UHCI Host Controller
[26746.291119] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[26746.291173] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000dce0
[26803.940139]  [<c0178f93>] cdev_get+0x33/0x50

user@user-laptop:~$ dmesg | grep CD
[26748.501696] hdc: TOSHIBA CD-ROM XM-1902B, ATAPI CD/DVD-ROM drive
[26749.002465] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[26749.002492] Uniform CD-ROM driver Revision: 3.20

---

### Post by sj3fk3 on 2007-07-04
> **FatFreddy said:**
> Hi guys,
user@user-laptop:~$ dmesg | grep cd
user@user-laptop:~$ dmesg | grep CD

Next time try dmesg | grep -i cd ;)

Anyway, this is very strange. Have you tried mounting the CD by hand?
sudo mount /dev/hdc /media/cdrom -t iso9660 

Does /media/cdrom0 exist?

---

### Post by FatFreddy on 2007-07-08
Hi,

Thanks for the response, I was beginning to think nobody would answer :-o

user@user-laptop:/media/cdrom0$ dmesg | grep -i cd
[   27.822321] hdc: TOSHIBA CD-ROM XM-1902B, ATAPI CD/DVD-ROM drive
[   28.159455] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   28.160166] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   28.160224] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000dce0
[   28.336419] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[   28.336445] Uniform CD-ROM driver Revision: 3.20
[   90.412562]  [<c0178f93>] cdev_get+0x33/0x50

user@user-laptop:/media/cdrom0$ sudo mount /dev/hdc /media/cdrom -t iso9660
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@user-laptop:/media/cdrom0$ cd /media/cdrom0
user@user-laptop:/media/cdrom0$ dir
user@user-laptop:/media/cdrom0$ ls -al
total 8
drwxr-xr-x 2 root root 4096 2002-05-30 23:13 .
drwxr-xr-x 4 root root 4096 2007-04-15 23:56 ..
user@user-laptop:/media/cdrom0$

---

### Post by sj3fk3 on 2007-07-08
> **FatFreddy said:**
> Hi,

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

Thats might be the problem, it has no support for the cdrom filesystem (iso 9660)

Try: grep iso /proc/filesystems
if there is no iso9660
try sudo modprobe iso9660
see if it's there with lsmod | grep iso
then try mounting again

---

### Post by FatFreddy on 2007-07-09
Hello sj3fk3,

Many thanks for the help, but still no joy :(

user@user-laptop:~$ grep iso /proc/filesystems
user@user-laptop:~$ sudo modprobe iso9660
Password:
user@user-laptop:~$ sudo modprobe iso9660
user@user-laptop:~$ lsmod | grep iso
isofs                  36284  0 
user@user-laptop:~$ sudo mount /dev/hdc /media/cdrom -t iso9660
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@user-laptop:~$

---

### Post by FatFreddy on 2007-07-09
Further to above...

user@user-laptop:~$ sudo mount /dev/hdc /media/cdrom -t iso9660
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@user-laptop:~$ dmesg | tail
[29723.861598] ide: failed opcode was: unknown
[29723.862372] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[29723.862388] end_request: I/O error, dev hdc, sector 64
[29723.863389] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[30161.156010] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[30161.156038] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[30161.156055] ide: failed opcode was: unknown
[30161.156829] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[30161.156845] end_request: I/O error, dev hdc, sector 64
[30161.156878] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
user@user-laptop:~$

---

### Post by sj3fk3 on 2007-07-09
> **FatFreddy said:**
> Hello sj3fk3,

Many thanks for the help, but still no joy :(

user@user-laptop:~$ lsmod | grep iso
isofs                  36284  0 
user@user-laptop:~$ sudo mount /dev/hdc /media/cdrom -t iso9660
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@user-laptop:~$

Ok, isofs is an alias if iso9660 so thats ok, you do have the module to read the cd-rom filesystem, you might have the same problem reported here [ [https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/22623](https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/22623) ]

Try
sudo mount -o norock,utf8 /media/cdrom

---

