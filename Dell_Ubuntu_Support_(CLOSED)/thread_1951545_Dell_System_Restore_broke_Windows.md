---
title: "Dell System Restore broke Windows"
date: 2012-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by exclipy on 2012-04-02
I'm trying to restore my Dell Studio 1535 back to the factory default so I can give it away - ie. remove the Ubuntu partitions and bring back Windows to the factory image.  I selected Windows on the Grub menu and pressed F8, then went through the process of a factory restore.  It claimed to have succeeded, but now the Grub menu comes back up on booting and when I select Windows, Grub gives me this error:

```
error: no such device: 2C5E84055E83C654
error: no such disk

Press any key to continue...
```

Here's some information about the partitions.  This is what fdisk -l /dev/sda tells me:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316        4963    29296875    7  HPFS/NTFS
/dev/sda4            4964       30401   204330704+   5  Extended
/dev/sda5            4964        5692     5855661   82  Linux swap / Solaris
/dev/sda6            5693        9339    29294496   83  Linux
/dev/sda7            9340       30401   169180483+  83  Linux
```

sda3 is the Windows partition and sda1/sda2 are hidden Dell system restore partitions.

I can still boot into Ubuntu OK.  Can anyone help me remove Ubuntu/Grub and bring back the Windows MBR?

---

### Post by jasonrisenburg on 2012-04-02
Do you have the original dell discs? If you do install them back t factory default. If not, well you have 2 option you can install a free os, (linux) or buy a new one. You may be able to contact dell and give them the serial number. They may be able to help.

---

### Post by exclipy on 2012-04-02
The computer didn't come with any disks.  And I need this done by the weekend, which probably means the disks won't have enough time to arrive in the mail if I order them.

---

### Post by CottonCandy on 2012-04-06
If you don't have the disks you can download & burn your own repair cd. [How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1") has links to download a repair disk for Vista and for 7 as well as the commands you need to type to fix the MBR.       

I'd try to fix the MBR first to make sure Windows still works.  Once you verify that Windows is working I would suggest removing Ubuntu by deleting the Ubuntu partition(s). You will probably have to fix the MBR again to remove Grub. (Try rebooting Windows after you delete the Ubuntu partition(s), if you get an error you need to fix the MBR again.)

---

