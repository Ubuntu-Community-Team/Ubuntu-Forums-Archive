---
title: "Dual boot windows option in grub menu gone"
date: 2009-03-09
forum: General Help
---

### Post by Yumi on 2009-03-09
I had/have a dual boot installation and after an upgrade to 8.10 the windows option in the grub menu disappeared. You see I do not use windows that often and did not notice.

How can I get this back by editing menu.lst?

Output from fdisk is (Windows is on sda1):
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3685        8267    36812947+  83  Linux
/dev/sda3            8268        9729    11743515    5  Extended
/dev/sda5            8514        9729     9767520    b  W95 FAT32
/dev/sda6            8268        8512     1967899+  82  Linux swap / Solaris

```


Just found the following entry on Feisty help. This might be it!
> title 		Windows XP
rootnoverify 	hd0,0
makeactive
chainloader +1

Michael

---

### Post by Elfy on 2009-03-09
Try adding this to the bottom of the menu list

```
sudo nano -B /boot/grub/menu.lst
```

```
title           Windows
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Yumi on 2009-03-09
Thanks for the good confirmation! I forgot the () around the drive. Would have been difficult.

Michael

---

