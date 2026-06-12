---
title: "Triple Boot Help (Ubuntu 8.10 - 32 bit/Vista32/Vista64)"
date: 2008-12-15
forum: General Help
---

### Post by snarpel on 2008-12-15
Hi everyone.

I am trying to triple boot Vista 32 bit, Vista 64bit, and Ubuntu 32 bit. I managed to get to Vista boot manager through Grub. After much googling, I was not able to find a solution to boot directly into Vista 32 and Vista 64 without going through Vista boot loader. Is it possibe to have 3 OS on Grub bypassing the Vista boot manger? 

When I boot into 32 bit partition, I am taken to the Vista boot loader. When I boot into 64 bit partition, I get error message "BOOTMGR is missing..."
Here are some outputs if they help.

sudo fdisk -l output:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eacd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16506   132579316    7  HPFS/NTFS (32 bit Vista)
/dev/sda2           16506       30402   111616000    7  HPFS/NTFS (64 bit Vista)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe28f324f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       54463   437473023+   7  HPFS/NTFS
/dev/sdb2           54464       60801    50909985    5  Extended
/dev/sdb5           54464       60536    48781341   83  Linux
/dev/sdb6           60537       60801     2128581   82  Linux swap / Solaris

```

menu.lst:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0ee8c024-9ae7-464f-8c4f-b0ecbc95594b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ee8c024-9ae7-464f-8c4f-b0ecbc95594b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0ee8c024-9ae7-464f-8c4f-b0ecbc95594b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ee8c024-9ae7-464f-8c4f-b0ecbc95594b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0ee8c024-9ae7-464f-8c4f-b0ecbc95594b
kernel		/boot/memtest86+.bin
quiet

# Vista 32-bit boots to Vista boot manager correctly
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1

# Vista 64-bit trying to skip Vista boot manager - did not work
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
chainloader	+1

```

---

### Post by TeXtonyx on 2008-12-15
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16506   132579316    7  HPFS/NTFS (32 bit Vista)
/dev/sda2           16506       30402   111616000    7  HPFS/NTFS (64 bit Vista)

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       54463   437473023+   7  HPFS/NTFS

----------------------

# Vista 32-bit boots to Vista boot manager correctly
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1

# Vista 64-bit trying to skip Vista boot manager - did not work
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
chainloader	+1

--------------------------------------

/dev/sdb1 is bootable, * , and NTFS; hd0 = sda and hd1 = sdb

root (hd1,0) means you are booting to sdb1 not sda1=(hd0,0) 
which you your comment refers to as  your 32 bit Vista. 

Your second entry (hd1,1) is sdb2, which fdisk reports as "Extended" 

(hd0,1) means sda2 which you say is your 64 bit Vista. 
The sda notation for partition one, is sda1, while the 
menu.lst boot notation for partition one is a 0
Your entries don't reflect this numbering difference.
You are booting Vista on second drive, nothing from first drive.

Also Vista 64bit partition is not marked with an * and I'm not
sure if that is a problem, or not.

Since you appear to have 3 bootable Vistas, it should look like this
root (hd0,0) sda1 supposedly 32 bit Vista
root (hd0,1) sda2 supposedly 64 bit Vista
root (hd1,0) sdb1 (boots) which you say boots Vista 32, but you don't 
describe that as such in your comments. You think it is sda1.
------------------------------------
You are now using
root (hd1,0) and think they are pointing to sda or first drive
root (hd1,1)
but these entries point to sdb, your second drive. Compare to my entries.
---------------------------------------------------------------

This can get tricky because Windows often migrates boot files
from two Windows partitions all onto one Vista partition. I 
think you should unhide and look at all the boot files on all
three partitions and make sure they each have separate boot files
and that there hasn't been any consolidation. I haven't booted
both Vista 32 and Vista 64 on the same drive and don't know how
that works. On two different drives, the boot files mostly stay put. 
There may be some boot files missing on sda for both partitions
having what belongs to them. Unhide hidden files and look it over.

---

### Post by caljohnsmith on 2008-12-15
In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info7.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup. As TeXtonyx all ready pointed out, most likely the boot files are mixed up at this point. If both of your Vista's are fresh installs, I would recommend simply reinstalling them, but make sure to "hide" the first Vista installation when you go to install the second Vista, because otherwise you won't be able to keep the two Vistas separate. After you are done installing the second Vista, then you should be able to safely unhide the first one and boot both from Grub. If you would like help with that, please post the output of the above script and we can work from there. :)

---

