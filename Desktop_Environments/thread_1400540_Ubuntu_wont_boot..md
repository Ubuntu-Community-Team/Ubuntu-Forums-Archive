---
title: "Ubuntu wont boot."
date: 2010-02-07
forum: Desktop Environments
---

### Post by SirRedTooth on 2010-02-07
Reccently I moved to ubuntu.
Using wubi I installed ubuntu making my system dual boot alongside vista.

Everything worked perfectly until I came to boot my system this morning and instead of having a list of different things to load on grub.
I got a command line.

So now whenever I choose to boot into ubuntu I get a command line.
How can I make it automatically boot into ubuntu or go back to the previous way where I had a selection of things to boot into,

---

### Post by SirRedTooth on 2010-02-07
Here is the error report I get when I boot from
/boot/vmlinuz-2.6.31-17-generic

(took me ages to write this down)
```
1.514265 md: autorun ...
1.514321 md: ... autorun DONE
1.51422 VFS: Cannot open root device "<NULL>" on unknown-block(104,1)
1.514583 Please append a correct "root=" boot option; here are the available partitions
1.514662 0800 156290904 sda driver: sd
1.514765 0801 8393931 sda1
1.514866 0802 134467580 sda2
1.514967 0803 13425604 sda3
1.515068 0500 1048575  sro driver
1.515170 Kernel panic not syncing: UFS : unable to mount root fs on unknown-block(104,1)
1.515245 Pid: 1, comm: swapper Not tainted 2.6.31.17generic #54-Ubuntu
1.515366 Call trace:
1.515368 [<056e92c7>] ? prinok+0x1810x1c
1.515428 [<8056e870>] mount-block-root+0x1d910x272
1.515550 [<c01f30f7>] ? sys-mknod+0x2710x30
1.515610 [<c078ede57>] mount-root+0x5910x5f
1.515671 [<c078ef39>] prepare_namespace+0x14e10x188
1.515732 [<c01e63bo>] ? sys-access+0x2010x30
1.515794 [<1078e3fa>] Kernal-init+0xb210xbe
1.515854 ? Kernal-init+0x0/0xbe
1.515916 [<c0104007>] Kernal-thread-helper+0x1/0x10
```

---

### Post by SirRedTooth on 2010-02-07
I tried entering this following command into the grub commandline
> 
linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root/disk ro
boot

I then got this error message

> 
md: Scanned 0 and added 0 drives
md: autorun ...
md: ... autorun DONE
List of all partitions
0800 15629094 sda driver: sd
0801 8393931 sda1
0802 134467580 sda2
0803 13425664 sda3
0b00 1048575 sro driver: sr
No filesystem could mount root, tried ext3 ext2 ext4 fuseblk
Kernel panic -not syncing: VFS: unable to mount root fs on unknown block(8,1)

I didnt bother writing it after that but if you need to know the rest of the error message or the numbers at the start of each line (1.502109) tell me and I can get them =)

---

