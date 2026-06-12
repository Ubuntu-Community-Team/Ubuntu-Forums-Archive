---
title: "Kernel upgrade"
date: 2009-02-12
forum: General Help
---

### Post by CatmanITA on 2009-02-12
I am using Ubuntu 7.10 with kernel 2.6.22 and I need to upgrade it to 2.6.23
I managed to make the vmlinuz file, install the modules and create the intrd file, but when I boot my 2.6.23 kernel stops at:

> Waiting for root file system

check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

Here are the contents of the files:
/boot/grub/menu.lst:
> 
title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.22-16-generic root=UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 ro quiet splash
initrd		/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.22-16-generic root=UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 ro single
initrd		/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 ro single   
initrd		/initrd.img-2.6.22-14-generic

title		Linux 2.6.23
root		(hd0,7)
kernel		/vmlinuz-2.6.23 root=UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 ro single
initrd		/initrd.img-2.6.23

/etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=90a875bc-e871-48d1-bbb9-f2f0eca529d9 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=a680d661-3aff-4ec9-a3ba-5845499662cd /boot           ext2    defaults        0       2
# /dev/sda1
UUID=3007-17F2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=12EC2E5CEC2E3A7D /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=A02CFDED2CFDBDFA /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=d7ad3590-7202-446c-b644-b620bf8a35f8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0     0


All I found online about this problem is to change these two files, but comparing them they look fine to me. I tried to change the UUID to simple labeling, but that did not work either. Can anyone help? Thank you.

---

### Post by CatmanITA on 2009-02-16
Can anyone help?

---

