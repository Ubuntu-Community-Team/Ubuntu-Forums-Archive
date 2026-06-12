---
title: "Dual Boot problem - got my fdisk -l listing, any ideas?"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by gambler on 2007-08-13
Hey guys...

Just checking to see what my menu.lst file SHOULD look like with the following Windows Vista/Ubuntu dual boot attempt (I installed Ubuntu and it works fine.. I just can't access Vista).

Here's the fdisk -l output:

----------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11306    80260740    7  HPFS/NTFS
/dev/sda4           11307       19458    65473517    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6   *       11307       18810    60275817   83  Linux
/dev/sda7           18811       19130     2570368+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8192 * 512 = 4194304 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         248     1015280    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 255, 32) logical=(247, 223, 32)
---------------------------------------

It appears that Windows Boot Manager is on the /dev/sdb1 partition.

I thought a line like:

rootnoverify (hd1,0) would do the trick, but instead I get the error message: Error 21: Selected disk does not exist.

Any thoughts?

I can't get the "Repair Windows" function to work from the Windows Recovery disk as it doesn't show Windows being present at all, and the C: drive is unavailable to go into via the shell in the Vista Recovery CD, so I'm hoping I didn't actually format it!  Is there any way I can find this out?

---

### Post by sciurus on 2007-08-14
Could you explain where you think Windows is installed?

---

### Post by gambler on 2007-08-14
Actually, I have no idea anymore.  My guess, because fdisk /dev/sda4 doesn't work, is that Windows is installed there and that it's corrupted.

And I think the /dev/sdb1 drive was  the D: drive with the /Windows directory under Vista.  But I don't know if the Bootmgr.exe file was on D: or C:.

More weirdness happened though since I posted this.  After the umpteenth time playing with things and loading from the Recovery Disk, it actually found Windows and restarted.  I was so shocked that I forgot to hit F12 to boot from the CD, and when I went back in, I still had the same problem.. Windows doesn't appear as an operating system when I use the Recovery CD.  But, /dev/sdb1 has disappeared in the fdisk -l listing I posted.  Now it only shows the /dev/sda* lines, so the repair did _something_.  Oddly, now when using the Vista Recovery CD, sometimes the former 'D:' drive shows up on 'C:', but not always.  

This is just weird.

---

### Post by gambler on 2007-08-14
Ok... So I did manage to destroy my Vista partition... Discovered this with Gparted.  So we'll try a fresh install of both...

---

