---
title: "Grub: something ain't right"
date: 2009-04-04
forum: General Help
---

### Post by causeitsme on 2009-04-04
The problem started when I installed Arch linux on sda4. Couldn't boot anything. So after I couldn't get grub fixed with LiveCD I installed Ubuntu 8.04 over the Arch linux.
This fixed grub but was using (hd0,3) and I want grub to use menu.lst of (hd0,4), i.e. Ubuntu 8.10.

Now I can run:
```
ubuntu2hp@Ubuntu2HP:~$ sudo grub
[sudo] password for ubuntu2hp: 

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,3)
 (hd0,4)
grub> setup (hd0,4)
setup (hd0,4)

Error 12: Invalid device requested
grub> 
```

This is the fdisk -l
```
user@user-desktop:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7769    62404461   83  Linux
/dev/sda2           30314       30401      706860   82  Linux swap / Solaris
/dev/sda3           18238       30313    97000470    5  Extended
/dev/sda4   *        7770       18237    84084210   83  Linux
/dev/sda5           18238       30313    97000438+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9729    78148161   83  Linux
```

sda2 has Puppy linux 
sda4 has Ubuntu 8.04
sda5 has Ubuntu 8.10 (main OS)

This is /etc/fstab from the Ubuntu 8.10 system i.e. sda5 - (hd0,4)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=81167332-7c2f-47a9-a422-650cb222a378 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c130dbbb-74d5-4ad2-8b74-6faedb7b236b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=126,devmode=664	0	0
192.168.2.3/Guest /mnt/Guest smbfs username=Guest,password=password 0 0
```

I have used gparted to make sda5 have the boot flag and then run grub setup (hd0,4) and it gives the same result: Error 12: Invalid device requested. I then changed the boot flag back to sda4 to ensure I could reboot the computer.

So, how can I make grub use the menu.lst from the 8.10 install that resides on (hd0,4)?

---

### Post by adult swim on 2009-04-04
you added the partition to the setup step in grub.  to use the grub from sda5 run these ```
sudo grub

root (hd0,4)

setup (hd0)

quit

```

---

### Post by causeitsme on 2009-04-05
That did the trick! Thanks!!

---

