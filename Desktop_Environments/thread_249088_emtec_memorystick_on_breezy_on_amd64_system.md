---
title: "emtec memorystick on breezy on amd64 system"
date: 2006-09-02
forum: Desktop Environments
---

### Post by django_xl on 2006-09-02
Hi folks,

I have this emtec 512mb memorystick that I want to use on my ubuntu system on the amd64 platform. I'm running breezy and when I plug this memorystick in, I get the following messages in /var/log/messages:

Sep  2 09:36:24 localhost kernel: [ 1120.473095] usb 2-8: new high speed USB device using ehci_hcd and address 3
Sep  2 09:36:30 localhost kernel: [ 1123.879912] usb 2-8: new high speed USB device using ehci_hcd and address 4
Sep  2 09:36:35 localhost kernel: [ 1127.635406] usb 2-8: new high speed USB device using ehci_hcd and address 5
Sep  2 09:36:40 localhost kernel: [ 1130.452578] usb 2-8: new high speed USB device using ehci_hcd and address 6


My /etc/fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /boot           ext3    defaults        0       2
/dev/sda6       /tmp            ext3    defaults        0       2
/dev/sda8       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


And my /etc/mtab looks like:
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-amd64-generic/volatile tmpfs rw,mode=0755 0 0
/dev/sda5 /boot ext3 rw 0 0
/dev/sda6 /tmp ext3 rw 0 0
/dev/sda8 /usr ext3 rw 0 0
/dev/sda7 /var ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0


sudo /sbin/fdisk -l /dev/sda gives:

Schijf /dev/sda: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sda1   *           1        7296    58605088+  a5  FreeBSD
/dev/sda2            7297        7393      779152+  83  Linux
/dev/sda3            7394        7782     3124642+  82  Linux swap / Solaris
/dev/sda4            7783       14593    54709357+   5  Uitgebreid
/dev/sda5            7783        7788       48163+  83  Linux
/dev/sda6            7789        8153     2931831   83  Linux
/dev/sda7            8154        8761     4883728+  83  Linux
/dev/sda8            8762       14593    46845508+  83  Linux

What could be wrong?
Why doesn't ubunu detect it properly?
Hope somebody can help.

---

### Post by django_xl on 2006-09-02
No sweat...already solved this in FreeBSD. There I could mount the partition very easily after it was detected by the kernel and showed up in the dmesg.

Thanks for reading this though.

---

