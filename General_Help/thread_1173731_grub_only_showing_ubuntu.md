---
title: "grub only showing ubuntu"
date: 2009-05-30
forum: General Help
---

### Post by Holyalchemy on 2009-05-30
Hey guys, 

I finally got around to getting a second hdd to test out ubuntu this morning. I currently have fedora 10 installed on another drive. I made the punishable mistake of just skipping through the install without reading the pages, and as a result, I wiped over my fedora loader. 

The drive shows up when I do "sudo fdisk -l" It shows as below: (fedora is on the 250gb drive)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bd4115f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       30401   243995220   8e  Linux LVM

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88e788e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       45591   366209676   83  Linux
/dev/sdb2           45592       46084     3960022+   5  Extended
/dev/sdb5           45592       46084     3959991   82  Linux swap / Solaris

I can mount the disk, and it show's what I kernels I can boot and my grub settings. After reading both config files for fedora and ubuntu, they're set out differently. I tried putting the details into the ubuntu grub loader of fedora, it starts to boot until it tried to mount the root system, to which I get:

Creating root device.
Mounting root filesystem.
mount: could not find filesystem '/dev/root'

I am 100% certain I have missed a detail to input to get system to boot. I throw myself at your mercy, I know I have done something stupid, but am in need of assistance.


*Sorry for the story length post and apologies if this is elsewhere, I couldn't find anything that matched this fault.


Thanks,


Stephen.

---

### Post by Holyalchemy on 2009-05-30
One last part I forgot to add. Here is a copy of the boot options from /boot/grub/menu.lst

Do I need to add the UUID field into the fedora loader? If so, where do I get it and what is it for?

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            a2aca2f2-3656-44e8-8012-1a786a655d4d
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=a2aca2f2-3656-44e8-80$
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            a2aca2f2-3656-44e8-8012-1a786a655d4d
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=a2aca2f2-3656-44e8-80$
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            a2aca2f2-3656-44e8-8012-1a786a655d4d
kernel          /boot/memtest86+.bin
quiet

title         Fedora
root          (hd1,0)
kernel        /vmlinuz-2.6.27.24-170.2.68.fc10.i686 ro root=/dev/VolGroup00/$
initrd        /initrd-2.6.27.24-170.2.68.fc10.i686.img

Thanks,

Stephen.

---

### Post by logos34 on 2009-05-30
Looks like sda1 is the separate Fedora boot partition (which was default last time I looked, one of the few distros that does that, if I'm not mistaken)...You might try [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") entry format to chainload fedora grub menu:

> title        Fedora 
configfile   (hd0,0)/grub/menu.lst

or 

> title        Fedora 
configfile   (hd0,0)/boot/grub/menu.lst

If it works you'll have to go through an extra menu screen, but at least you won't have to worry about updating ubuntu grub after a fedora kernel update

---

### Post by QIII on 2009-05-30
DON'T add that UUID.

The uuid you see there is specifically for the Ubuntu partition.

---

### Post by Holyalchemy on 2009-05-30
Logos34, you're a legend mate. All working now.

Thanks,

Stephen.

---

### Post by logos34 on 2009-05-30
you bet.

have a good day (or tomorrow, since you're down under ;)

---

