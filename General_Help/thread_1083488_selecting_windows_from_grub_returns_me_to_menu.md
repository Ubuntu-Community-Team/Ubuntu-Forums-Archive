---
title: "selecting windows from grub returns me to menu"
date: 2009-03-01
forum: General Help
---

### Post by islan on 2009-03-01
Here is my fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x492d492d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241199878+  83  Linux
/dev/sda2           30029       30401     2996122+   5  Extended
/dev/sda5           30029       30401     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdabddabd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

According to this, /dev/sda is Linux, and /dev/sdb is Windows.  And here is my /boot/grub/device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

And here is how my menu.lst looks for Windows:

title		Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

I have also tried rootnoverify (hd0,0), to the same effect.  The Linux HDD is SATA, while the Windows HDD is IDE.

PS:  I had to reinstall grub after installing Windows, using grub-install --root-device=/mnt(/dev/sda1)/boot /dev/sda

---

### Post by islan on 2009-03-01
bump

---

### Post by caljohnsmith on 2009-03-01
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by islan on 2009-03-02
Okay ... it seems to have fixed itself *scratches head*

---

