---
title: "My fstab"
date: 2006-01-09
forum: General Help
---

### Post by noeluylee on 2006-01-09
Hi, I jusy wondering if my fstab is correct, (see below) coz when I install this Ubuntu (with kde) i did manual partition and I manually add the swap and made it logical. below is my fstab, kindly check and let me know if something is wrong.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hda6       /media/Data     vfat    iocharset=utf8,umask=000   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

the reason im begining to wonder because I am having a problem with mounting my external drives.

1st. when I plug my external hard drive (usb) I encounter this error:
   An error occurred while loading media:/sdb1:
   The file or folder media:/sdb1 does not exist.
-but I can browse my file.
here's the result of fdisk -l
  Disk /dev/sdb: 40.0 GB, 40007761920 bytes 
  255 heads, 63 sectors/track, 4864 cylinders 
  Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
  /dev/sdb1               2        4864    39062047+   f  W95 Ext'd (LBA)
  /dev/sdb5               2        4864    39062016    b  W95 FAT32
- i figure out that it mounts on both sdb1 and sdb5, is that correct? this might have something to do with the error i encounter.

2nd. when I plug my digital camera, nothings happened. no result on fdisk -l. but i can see it on KControl > Peripheral > Camera.

hope somebody could help me. im stuck!

Thanks.

---

### Post by feathers on 2006-01-09
I think it is a kde problem. Go to the folder /media/sda1 or /media/whateverdevice and see if you can access your files this way.

---

### Post by noeluylee on 2006-01-09
After i plugged my external hard disks, it mounted on both sda1 and sda5

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        4864    39062047+   f  W95 Ext'd (LBA)
/dev/sda5               2        4864    39062016    b  W95 FAT32

I cannot see it on /media.. i path it to /dev and I found both sda1 and sda5 but it said to be a file, not a folder, thus I cannot browse the content.

I wonder why it boots on 2 device? :) any clue on this?

what I really wanted to solve now is my camera, doesnt mount at all, it detect but not mount =( my prior kubuntu does mount my camera, i re-install everything from scratch, and now it doesnt mount anymore... will appreciate any suggestion.. :)

Thanks.

---

### Post by feathers on 2006-01-10
I don't think it mounted the disk. This seems to be the information message that you have plugged in something and what it is. There are two devices because you have an extended partition which is recognizes seperately. You cannot browse any file in the /dev folder. They just represent devices and only the kernel can access them. 
Now try this: Plug in your harddrive and type: sudo mount -t vfat /dev/sda5 /mnt. Go to /mnt and look if you see any files. 
If it works do this to unmount the drive: sudo umount /dev/sda5
Does this work?

---

### Post by noeluylee on 2006-01-10
I can browse the content of my hard disk upon checking /mnt > ls.. but even if i dont do sudo mount -t vfat /dev/sda5 /mnt i can browse my hard disk. All I want is to get rid of this error message... even it showed this error i still can browse my ext. hard disk thru konqueror browser
An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

I am getting frustrated with my digital camera, I still cant solve the problem.  my camera doesnt seem to mount once i plugged it in. but my computer detects the camera, (on kcontrol).. on ubuntu (on the same computer, same kernel) its detects my camera, once I plugged in the digital camera, it opens a program that showed me the content of the camera. 

Hope that somebody could help me to fix this problem.

---

### Post by feathers on 2006-01-10
Maybe you can set a link from sdb1 to whereever your harddisk is mounted automatically. As to the camera. I thinks you can't mount it but you can download pictures using digikam.

---

### Post by wizzkid on 2006-01-10
digikam work quite well :)

---

### Post by noeluylee on 2006-01-11
Thanks. digikam works :)

---

