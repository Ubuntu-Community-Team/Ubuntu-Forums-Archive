---
title: "Hibernate and suspend no longer working"
date: 2009-02-20
forum: General Help
---

### Post by matt_wood87 on 2009-02-20
Hi guys,

until recently my acer travelmate 5720 running Ubuntu 8.10 would happily sleep or hibernate when asked.

recently i've noticed that neither of these functions work any more. if i hibernate or suspend/sleep then when i try to resume the computer just shuts down.

if anyone could suggest how i should go about fixing this issue i'd be very greatful. unfortunately i can't be any more specific about when or why it stopped working as i only recently noticed it.

many thanks for looking.

matt

---

### Post by matt_wood87 on 2009-04-01
having done a bit more research, it may have something to do with my fstab file, and usuage of the swap partition, could someone who knows a bit more about this than me, compare my print out of my partitions on my disk to the contents of my fstab file.

matthew@mtw:~$ sudo parted /dev/sda print
Model: ATA WDC WD1600BEVS-2 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      5248MB  139GB  134GB   primary  ntfs         boot 
 2      139GB   141GB  1982MB  primary  linux-swap        
 4      141GB   160GB  19.0GB  primary  ext3              



fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=de0122aa-71e0-4f56-b848-64f8bbb464ff /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=16D9-B5D2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=14FAE0CEFAE0AD64 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=fb22cf71-ee4b-48ca-a3b0-164ffc5e109a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



thanks for your help!

Matt

---

