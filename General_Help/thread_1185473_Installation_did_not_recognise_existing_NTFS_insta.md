---
title: "Installation did not recognise existing NTFS installations! Please help!"
date: 2009-06-12
forum: General Help
---

### Post by Pipps on 2009-06-12
I had a new hard drive with the following two NTFS filesystems already in place:

sda1 NTFS WinXP(1) 350GB
sda2 NTFS WinXP(2) 100GB
Free space          50GB (Extended partition)

(I am forced to use the two XP filesystems for work tasks.)

I installed Ubuntu onto the remaining 50GB free space, creating the relevant partitions for '/boot', 'swap' and '/' on respective logical partitions within the above extended partition. Installation completed successfully.

However, when the Grub bootloader launched at the next system startup, it was apparent that Grub had not recognised or referenced the two existing XP installations. Neither of those existing installations appear in the Grub boot options. 

Both of those installations had booted from scratch with no problems, prior to installing Ubuntu and Grub.

Furthermore, on booting into LiveUSB again, I go try to navigate to the menu.lst file by going to '/boot/grub', only to find that there is no '/grub' folder in the '/boot' directory of my new Ubuntu installation.

How can I rectify the problem of Grub not recognising and allowing me the option to boot either of my two existing XP filesystems?

---

### Post by colau on 2009-06-12
> **Pipps said:**
> I had a new hard drive with the following two NTFS filesystems already in place:

sda1 NTFS WinXP(1) 350GB
sda2 NTFS WinXP(2) 100GB
Free space          50GB (Extended partition)

(I am forced to use the two XP filesystems for work tasks.)

I installed Ubuntu onto the remaining 50GB free space, creating the relevant partitions for '/boot', 'swap' and '/' on respective logical partitions within the above extended partition. Installation completed successfully.

However, when the Grub bootloader launched at the next system startup, it was apparent that Grub had not recognised or referenced the two existing XP installations. Neither of those existing installations appear in the Grub boot options. 

Both of those installations had booted from scratch with no problems, prior to installing Ubuntu and Grub.

Furthermore, on booting into LiveUSB again, I go try to navigate to the menu.lst file by going to '/boot/grub', only to find that there is no '/grub' folder in the '/boot' directory of my new Ubuntu installation.

How can I rectify the problem of Grub not recognising and allowing me the option to boot either of my two existing XP filesystems?

Can you post 
```

sudo fdisk -l

```

---

### Post by Pipps on 2009-06-12
Yes, with pleasure.

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedf4edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       44619   358402086    7  HPFS/NTFS
/dev/sda2           44620       58889   114623775    7  HPFS/NTFS
/dev/sda3           58890       60801    15358140    5  Extended
/dev/sda5           58890       60552    13358016   83  Linux
/dev/sda6           60553       60558       48163+  83  Linux
/dev/sda7           60559       60801     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae82b228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1002 MB, 1002438656 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x006beaa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      978912+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 222, 37)

```

I await your next response. Thank you.

---

### Post by statistic on 2009-06-12
This may sounds stupid or obvious, but it sounds like you're trying to modify the menu.lst while booted in the live usb instead of your consistent partition? I may be missing something so I apologize if this is unproductive.

Just boot into the linux partition and change the menu.lst file there, all the live cds/usbs dont have grub on them, so you wouldn't find a /boot/grub folder.

If you are having trouble booting into the installed linux partition, use the live usb and mount the installation, then edit the /boot/grub/menu.lst from there inside that mounted directory. So like /mnt/yourLinux/boot/grub/menu.lst

---

