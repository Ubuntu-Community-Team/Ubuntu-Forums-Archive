---
title: "GRUB: executable error when trying to boot on my windows partition"
date: 2009-03-23
forum: General Help
---

### Post by Fixman on 2009-03-23
This is the windows section of my menu.lst:

```
 title Windows
root (hd1,0)
chainloader +1
savedefault 0 
```

However, each time I try to boot from it (more specifically when it chainloads), it tells me something about bad executable and doesn't let me boot.

For curiosers, this is my fdisk:

```
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS 
```

---

### Post by Xiong Chiamiov on 2009-03-23
Your code looks to be correct.  Can you boot into Windows directly (if you change settings in your BIOS or change jumpers)?  What about using Super Grub Disk?  How often do you boot into Windows, and when did you notice this?

---

### Post by meierfra. on 2009-03-23
Add both of these to menu.lst

title Windows (hd0)
root (hd0,0)
chainloader +1


title Windows  (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Reboot. Try both titles. If one of them works, you can deleted the others from menu.lst

If none of them works, report any error messages you got.

---

