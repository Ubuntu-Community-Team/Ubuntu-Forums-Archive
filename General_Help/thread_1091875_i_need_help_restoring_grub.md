---
title: "i need help restoring grub"
date: 2009-03-09
forum: General Help
---

### Post by slappy95633 on 2009-03-09
ok so i am trying to dual boot windows and ubuntu. I had windows installed and then installed ubuntu 8.10 and something happend to my copy of windows. so i reloaded and i fallowed the directions on this site to reload grub
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) and it sayed it worked and everything went fine but i don't get grub it still just boots to xp. here is some info on my setup

for fdisk:
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27bfc8e3

Device Boot Start End Blocks Id System
/dev/sda1 * 1 24320 195350368+ 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7543b3e

Device Boot Start End Blocks Id System
/dev/sdb1 1 7834 62926573+ 5 Extended
/dev/sdb2 7835 13054 41929650 7 HPFS/NTFS
/dev/sdb3 * 13055 60801 383527777+ 7 HPFS/NTFS
/dev/sdb5 1 373 2996028 82 Linux swap / Solaris
/dev/sdb6 374 7834 59930451 83 Linux




so when i do what that site tells me then i should do 

>root (hd1,5)
>setup (hd1)

right ??? that should do it shoudldent it please help

---

### Post by slappy95633 on 2009-03-09
bump any one with any ideas

---

### Post by slappy95633 on 2009-03-09
bump please i need help

---

### Post by mandeepsmagh on 2009-03-09
Follow this link : - [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351"). This should help u.

---

### Post by slappy95633 on 2009-03-09
yes thanks i got grub working now i am having troubles booting into windows look here please [http://ubuntuforums.org/showthread.php?t=1056606](http://ubuntuforums.org/showthread.php?t=1056606)

---

