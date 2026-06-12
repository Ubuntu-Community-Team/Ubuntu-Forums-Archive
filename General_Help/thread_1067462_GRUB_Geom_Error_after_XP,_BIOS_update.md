---
title: "GRUB Geom Error after XP, BIOS update"
date: 2009-02-11
forum: General Help
---

### Post by fmhoyt on 2009-02-11
Hi,

I have a Ubuntu Intrepid/XP dual boot setup on a Thinkpad T61 amd64. Intrepid is fully updated as of today (2/11/09). Things have been working fine, until this evening when I updated XP and the Thinkpad BIOS software. Now at startup grub stops at: 

GRUP Geom Error

I have tried booting from the live CD and doing the [the following]("http://ubuntuforums.org/showthread.php?t=1067378&highlight=grub"):


$ sudo grub 
> root (hd0,0)
> setup (hd0)
> quit

This fails at the "setup (hd0)" command, which returns an error message to the effect of "partition cannot be found." 

Thanks in advance for suggestions.

---

### Post by caljohnsmith on 2009-02-11
How about posting the output of:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by fmhoyt on 2009-02-11
> **caljohnsmith said:**
> How about posting the output of:
```
sudo fdisk -lu
```
And please identify your partitions.

Here's the output: 

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc54fb6e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    86204852    43102395    7  HPFS/NTFS
/dev/sda2        86220855   190820069    52299607+  83  Linux
/dev/sda3       190820070   195366464     2273197+   5  Extended
/dev/sda5       190820133   195366464     2273166   82  Linux swap / Solaris
```

Not sure what you mean by "identify [my] partitions," but if I understand right, sda1 is the XP partition, and sda2 is the Ubuntu file system. The others I think are self evident?

---

### Post by fmhoyt on 2009-02-12
I seem to have fixed the problem. There was an error in the grub re-installation procedure that I linked to above. 

Here's what worked (in session booted from Intrepid LiveCD): 

```
$ sudo grub
> find /boot/grub/stage1
  find /boot/grub/stage1 
   (hd0,1)
   (hd1,0)
> root (hd0,1)
> setup (hd0)
> quit
$ restart 
```

My problem was that I was entering the following, there being no such address: 

```
> root (hd0,0)
> setup (hd0)
```

---

### Post by caljohnsmith on 2009-02-12
Glad you got it figured out, I suspected your problem was that your Ubuntu partition wasn't sda1 or (hd0,0). Cheers and enjoy your Ubuntu install.

---

