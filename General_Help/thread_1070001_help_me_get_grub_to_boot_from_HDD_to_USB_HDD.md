---
title: "help me get grub to boot from HDD to USB HDD"
date: 2009-02-14
forum: General Help
---

### Post by sojojo on 2009-02-14
A quick question. I have mandriva on my USB HDD with a LILO boot loader and Ubuntu on my SATA hard drive with a Windows XP Partition. grub set up Ubuntu and Windows XP nicely, but I can't boot directly into the USB (mandriva) from grub. I have to do it from my bios which is kind of a pain (I'd like it all to be a little more seamless). Any ideas how i might go about doing that? I've found surprisingly few tutorials about this, and any help would be fantastic.

One weird thing is that there are all these extra non booting entries that look like this in menu.lst :
title		linux (on /dev/sdc5)
root		(hd2,4)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=7b685f25-50ff-49f9-9f85-3cc7f7d0b679 resume=UUID=4d1a20ee-089b-4731-b476-bf7e7de5aa8f splash=silent vga=788 
initrd		(hd0,4)/boot/initrd.img
savedefault
boot

---

### Post by logos34 on 2009-02-14
Post your 

sudo fdisk -l

You can try adding a ['chainloader' mandriva boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader") to ubuntu menu.lst.

---

### Post by sojojo on 2009-02-14
Thanks! Here it is. sdb is the external drive. I was contemplating chain loading once i read about it while investigating grub, but how do I figure out which name grub is assigning to that partition on my external? i.e (hd2,1) There's got to be a better way than trial and error :-k

Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1439    11558736    7  HPFS/NTFS
/dev/sda2            1440       30401   232629232    f  Extended LBA
/dev/sda5            1441       20484   152962897    7  HPFS/NTFS
/dev/sda6           20485       30048    76814797   83  Linux
/dev/sda7           30049       30401     2827440   82  Linux swap

Disk /dev/sdb: 120 GB, 120031511040 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb2               1        2678    21503002    5  Extended
/dev/sdb5               1        1019     8177085   83  Linux
/dev/sdb6            1020        1436     3341520   82  Linux swap
/dev/sdb7            1437        2678     9968332   83  Linux
/dev/sdb1   *        2679       14593   117133884    7  HPFS/NTFS

---

### Post by logos34 on 2009-02-14
> /dev/sdb5 1 1019 8177085 83 Linux

I believe that is Mandriva / partition, so you want

> title Mandriva
root (hd1,4)
chainloader +1

That or

> root (hd1)

to chainload mbr

---

### Post by sojojo on 2009-02-14
hey yeah, you're right about the drive name. I figured it out independently by snooping around a little and ended up just bypassing the second bootloader on the external drive (who needs 2 right?) One question.. if I unplug this external hard drive (I do from time to time), grub assigns hard drive names dynamically so, will that screw things up if I decide to add more drives later on (i.e. I have another external drive). 
Anyway, this is what I changed in menu.lst:
title           Mandriva USB
root            (hd1,4)
kernel          /boot/vmlinuz BOOT_IMAGE=linux root=UUID=7b685f25-50ff-49f9-9f85-3cc7f7d0b679 resume=UUID=4d1a20ee-089b-4731-b476-bf7e7de5aa8f splash=silent vga=788
initrd          (hd1,4)/boot/initrd.img
savedefault
boot

---

