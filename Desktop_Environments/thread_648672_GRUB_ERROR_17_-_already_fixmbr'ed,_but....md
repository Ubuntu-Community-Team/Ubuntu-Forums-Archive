---
title: "GRUB ERROR 17 - already fixmbr'ed, but..."
date: 2007-12-23
forum: Desktop Environments
---

### Post by shadow_waker on 2007-12-23
so i recently tried to install a new operating system, so i used the hard drive that had ubuntu on it, since i don't use ubuntu on my desktop anymore.  the installation failed ( :( ), and when i rebooted, i got a grub error 17.  i searched it up and found the fixmbr solution and tried it out.  i put in my xp cd and went to the recovery console and used fixmbr and then it asked which hard drive to use it on.  i ended up doing it on all three (hopefully wasn't a bad move... please), but when i boot it up again, it goes straight to a recovery partition that was already installed when we got the comp and goes to some recovery options of completely wiping the hard drive (which i really, really don't want to do), etc.  i also tried bootcfg to search for my os, but it says it doesn't find anything.  to check if all my files were still there, i used an ubuntu live cd to check up on my hard drives, and everything's still there.  i tried to reinstall ubuntu on the hd it was on before, i get a message saying the hd is corrupt...  my question is, is there a way to fix the way my comp boots, or did i do something very, very wrong?  @_@  if anyone can help, that would be great.  thanks in advance!

---

### Post by meierfra on 2007-12-23
Boot from the Ubuntu LiveCD, open a terminal (Apllications->Accessories->Terminal). Type

```
sudo fdisk -l
```

and post the output.

---

### Post by shadow_waker on 2007-12-23
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             563       19457   151774087+   7  HPFS/NTFS
/dev/hda2   *           1         562     4514233+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/hdd: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         743     5968116   83  Linux
/dev/hdd2             744         784      329332+   5  Extended
/dev/hdd5             744         784      329301   82  Linux swap / Solaris


my main operating system (windows xp) is on hda1.

---

### Post by meierfra on 2007-12-23
The boot flag is on hda2. You need to change it to hda1:

In a terminal in the LiveCD:

```
sudo grub
```
and at the "grub>" prompt
```

root (hd0,0)
makeactive
quit
```

I'm not sure that this be enough to fix your booting problem. But it  should be a step in the right direction.

---

### Post by shadow_waker on 2007-12-24
nice!  it work perfectly now, thanks!

---

### Post by meierfra on 2007-12-24
> nice! it work perfectly now, thanks! 

Glad to be of help.

---

