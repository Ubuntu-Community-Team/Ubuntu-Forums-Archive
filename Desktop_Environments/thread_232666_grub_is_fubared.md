---
title: "grub is fubared"
date: 2006-08-09
forum: Desktop Environments
---

### Post by tokez on 2006-08-09
hey guys--

somehow my grub menu deleted my windows xp entry after an update so i thought it wise to 'grub=install' to auto-detect windows. sounds funny huh? it doesnt work that easy:P

after some command surfing i got my linux to boot using the grub built in command line. however, my menu.lst is completely annhilated an doesnt boot linux or windows xp. i am posting my 'df' response and 'fdisk -l' response.

please help me fix this.

PS: windows is located on the first harddrive, second parition.
Linux is on the first hard drive, first partition.

df -
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc1             58601116  52859640   3955372  94% /
varrun                  907808        16    907792   1% /var/run
varlock                 907808         4    907804   1% /var/lock
udev                    907808       116    907692   1% /dev
devshm                  907808        16    907792   1% /dev/shm
lrm                     907808     18856    888952   3% /lib/modules/2.6.15-26-386/volatile

```

fdisk -l  -
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        7412    59536858+  83  Linux
/dev/hdc2   *        7413        9335    15446497+   c  W95 FAT32 (LBA)
/dev/hdc3            9336        9733     3196935    5  Extended
/dev/hdc5            9336        9733     3196903+  82  Linux swap / Solaris

```

---

### Post by tokez on 2006-08-09
possibly posted in the wrong forum .. heh my apologies

---

### Post by h00s on 2006-08-09
Hi!

You should not reinstall grub. Yes, update deleted the windows section from grub, but it copied before to menu.lst_backup (or something similar to this).

Boot as recovery, find backup of menu.lst with windows section in it, replace with damaged menu.lst.

---

### Post by Tomosaur on 2006-08-09
You should first run 'update-grub' rather than install, as it simply scans for new OSs, kernels etc, and sorts out your menu.lst.

---

