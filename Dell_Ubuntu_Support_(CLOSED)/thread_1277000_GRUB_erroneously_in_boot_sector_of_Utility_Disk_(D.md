---
title: "GRUB erroneously in boot sector of Utility Disk (Dimension E510)"
date: 2009-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlbakker on 2009-09-27
Hello all,

When installing Ubuntu 9.04 it changed the "boot sector" of the Utility Disk. :(
WinXP starts fine, uninterrupted by GRUB, but when booting from the Utility Disk I only see "GRUB".

I included below some further details I hope are relevant.

I hope to achieve the following but don't know where to start:

- restore the "boot sector" of the Utility Disk such that I can run the system diagnostics (without reinstalling everything, please). Alternativelly, can I get these system diagnostics on a CD from Dell?

- properly install grub (I assume) in /dev/sda3 such that I have the choice to boot Ubuntu in (I assume) /dev/sda7

Thanks for any help in this ...

When using the Live CD I can mount the partition with Ubuntu in it: "sudo mount /dev/sda7 /mnt/root".

When performing
> sudo grub
> find **/boot/grub/stage1**
>  (hd0,6)

I also did:
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8       13985   112278285    f  W95 Ext'd (LBA)
/dev/sda3   *       13986       18845    39037950    7  HPFS/NTFS
/dev/sda4           18846       19451     4867695   db  CP/M / CTOS / ...
/dev/sda5               8       12500   100349991    7  HPFS/NTFS
/dev/sda6           12501       12769     2160711   82  Linux swap / Solaris
/dev/sda7           12770       13985     9767488+  83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2               8       13985   112278285    f  W95 Ext'd (LBA)
/dev/sdb3   *       13986       18845    39037950    7  HPFS/NTFS
/dev/sdb4           18846       19451     4867695   db  CP/M / CTOS / ...
/dev/sdb5               8       12500   100349991    7  HPFS/NTFS
/dev/sdb6           12501       13985    11928231    e  W95 FAT16 (LBA)

---

### Post by jlbakker on 2009-10-03
Bump

---

### Post by jlbakker on 2009-10-03
I found a CD with the Utility Disk software on it.
So, one problem left. How to make my Dell a dualboot PC that can start windows XP and Ubuntu?

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8       13985   112278285    f  W95 Ext'd (LBA)
/dev/sda3   *       13986       18845    39037950    7  HPFS/NTFS
/dev/sda4           18846       19451     4867695   db  CP/M / CTOS / ...
/dev/sda5               8       12500   100349991    7  HPFS/NTFS
/dev/sda6           12501       12769     2160711   82  Linux swap / Solaris
/dev/sda7           12770       13985     9767488+  83  Linux

Windows XP is on Sda3 and Linux is on sda7. So far it seems GRUB modified the boot record of sda1 (with the "utility disk/partition".
I think I have to either make sda7 bootable or have grub modify the bootrecord of sda3?
I welcome hints/suggestions.

---

### Post by Bill Vincenti on 2011-05-21
Hello All, I am very new here. I installed Ubuntu 11.04 side-by-side with Windows XP Home Edition on an old Dell Dimension 2400 pc 80GB hd without any problems. Dell had a first partition (utility partition as I found out the hard way) FAT(16bit) 31MB originally so when I reinstalled Windows on this drive, I formatted first partition 31MB FAT, 2nd partion 26 GB NTFS which I installed Windows XP Home and left the remaining 44GB unallocated. I installed Ubuntu in this however, when it was done Windows doesn't recognize the EXT4 partition (I guess because there were already 2 parts and Linux needed 3 (of 4 max?) else Linux creates an extended part inside the Linux part - so I did not get an "E" drive visible from Windows XP so can't retrieve any files to swap when booted up to Windows. Windows wouldn't let me remove the 31MB FAT16 part but Linux would - so I did - and found out Windows was dependent on this little partition to load some root files. 
Is there any way i can find these missing files and put them into the root of the NTFS so that Windows will boot up strictly from the NTFS partiton without having to reinstall Windows and starting all over again? I need windows running on this pc as it is part of a Windows network for now. If I have to reinstall Windows, I believe the Dell disc allows me to install everything in NTFS without creating that little 31MB partition which would have avoided this problem in the first place however, I'm talking about a 2002 version, takes about 3 days to update all Windows stuff... THANK YOU IF ANYONE CAN HELP ME.

---

### Post by oldfred on 2011-05-21
@   	Bill Vincenti
Welcome to the forums.

Please start your own thread as your issue is not the same. (Most boot issues are not.) And post from a liveCD or your Ubuntu this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

