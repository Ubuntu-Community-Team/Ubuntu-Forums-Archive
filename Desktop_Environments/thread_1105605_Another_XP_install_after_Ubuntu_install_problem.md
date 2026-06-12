---
title: "Another XP install after Ubuntu install problem"
date: 2009-03-24
forum: Desktop Environments
---

### Post by grindedrick on 2009-03-24
Sorry for adding to the heap of similar problems but I've been reading and attempting trial by error all day.

I reinstalled XP then ran the live disk.
At the shell I typed:
```

sudo grub
find /boot/grub/stage1
root (hd1,0) ### since this is what the find command returned
setup (hd0)
quit

```

Well this seems to corrupt my XP partition which I believe to be at hd0,0.

When I boot from my XP disk the partition is unknown and when I try the repair console bootcfg /repair returns an error as does
chkdsk

I tried reinstalling windows and starting over just to get the exact same results.

When I leave the menu.lst file unedited I get unknown filesystem on partition 0x7 or something along those lines. I've also tried editing the menu.lst file several different ways with no progress. It seems it always restarts the GRUB. I haven't tried any unhide or map commands in the menu.lst file as I don't see they should be needed if my XP partition is sitting on hd0,0

I have 2 SATA hard drives and
Here's my fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa5faa5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a3a4a3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15935   127997856   83  Linux
/dev/sdb2           15936       29958   112639747+  83  Linux
/dev/sdb3           29959       30401     3558397+  82  Linux swap / Solaris

```

My current menu.lst stanza is:
rootnoverify (hd0,0)
chainloader +1
boot

Can somebody help me?
I've been tempted to reinstall XP once again and give the Super Grub a try.
Thanks in advance.

---

### Post by grindedrick on 2009-03-25
Since Windows likes (or HAS TO BE) the first partition on the first disk, then it seems putting the Grub on this MBR would mess Windows up. I imagine it would be better to create another MBR on my second hard drive and setup (hd1) there.

Well since my Linux filesystem starts on the first block I guess that's not an option. There's no way I'm gambling with corrupting my Linux system.

I went ahead with another XP install and tried Auto Super Grub. 
It would boot XP but not Ubuntu.
So I went and put the Super Grub on cd and this seems to be the only way I can boot both filesystems.

I don't know if that counts as fixing the problem so if anybody else has figured out something better please share.

---

