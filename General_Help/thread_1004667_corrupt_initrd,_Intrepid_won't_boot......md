---
title: "corrupt initrd, Intrepid won't boot....."
date: 2008-12-07
forum: General Help
---

### Post by tlesinsk on 2008-12-07
Hi all !

Sorry to step in with my crappy self-inflicted problem, but I really need some help on this one....

My laptop was recently rendered unworkable by a boot problem. I think I understand the problem by don't know where to start to fix it, so any help is *greatly* appreciated. Here we go:

I recently installed Kubuntu 8.10 Intrepid on my laptop using a net install. The problem is that the CD/DVD drive is dead (hardly ever used it anyway) and the BIOS ignores bootable USB drives. The only one I have that it would detect at all (but refuses to boot on) was an old 256MB one, on which I put the minimal debian/ubuntu network installer using unetbootin.

On the install I had before (Kubuntu 7.04 Feisty) I added an option in grub to boot on this stick and installed Intrepid that way. (I didn't want to go through all the incremental upgrades, and the 7.04->7.10 upgrade path was broken last week anyway...). As grub would crash when installing it, I asked the installer to put LILO instead. My hard drive is partitioned as

sda1 : /boot
sda2 : /
(then swap, home...)

SO -- just for you to get an idea of the mess I'm handling :)

After the install, i had problems with the drivers for my wireless (RaLink RT2500), so I decided to "manually" compile another version of the driver (RT2500 legacy from CVS). I *think* this is the source of my 
problem. After restarting the box, the boot sequence would end up with the following messages (copy-typed by hand...)

[    2.048095] RAMDISK: Compressed image found at block 0
[    2.394008] invalid compressed format (err=2)
[    2.447976] VFS: Cannot open root device "sda2" or unknown-block(0,0)
[    2.448054] Please append a correct "root=" boot option; here are the available partitions:
[    2.448131] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

It seems that the init ramdisk got corrupt, which prevents the kernel from having the module(s) necessary for accessing the hard drive and mounting the boot partition. The problem is, I have no other way to boot the box. The only way to solve this that I could think of are:

1- Make lilo boot another kernel. I have two kernels installed in my /boot, the other one might be working, but it's not in lilo.conf. Is there a way to boot it from the LILO boot prompt ?
2- Make lilo boot the aforementioned flash drive, same question...
3- Put the hard drive in an external enclosure and use another box to fix the initrd, but I dont't really know how to do it.

Any ideas/comments/advice ?

Thanks in advance !

T.

---

### Post by tlesinsk on 2008-12-08
Up ? :confused:

---

### Post by orrorin on 2008-12-08
don't know about LILO, but if it was grub, I'dve recommended trying each command from grub.conf manually. i.e. try running each command individually so you know which one fails specifically.

Generally speaking though, it looks like the boot roots are messed up somewhere.

---

