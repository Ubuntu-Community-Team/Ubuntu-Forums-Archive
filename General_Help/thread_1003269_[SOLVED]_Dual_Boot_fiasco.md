---
title: "[SOLVED] Dual Boot fiasco"
date: 2008-12-05
forum: General Help
---

### Post by morty35 on 2008-12-05
I have a desktop that has two hard drives.  The first is 14.7 GB and the second is 190 GB.  My computer was an XP only machine, but I got a virus.  
   I decided to switch to Linux primarily, but I have software that only runs on XP.  So I did a dual-boot.  I erased the first drive (which used to have XP operating system) because I wanted to install windows and XP on the second drive since it is much larger.
   I got the linux to work on the second drive (hd1,0) with no problems.  Afterward, I installed the Windows on a second partition on the second drive (hd1,1).  
   Now when I try to start the computer it says there is no NTloader.  I guess that was in the first harddrive and got deleted and when I installed windows it didn't create a new one.  
   I thought no biggie, it won't matter when I restore the grub boot loader.  I did the following commands to restore grub:

$ find /boot/grub/stage1
(hd1,0)
$ root (hd1,0)
$ setup (hd1)
$ quit

When I start the machine it still says the NTloader is missing?  I think it is because the computer still thinks to check the first drive for the NTloader.  

So how do I restore the grub loader so that I can use my computer without the loadup disk?

Here is the configuration:

hd0 - no operating system.  Just formatted NTFS and the location of my files in case the partitioning didn't work.  

hd1,0 Linux
hd1,1 XP

---

### Post by Herman on 2008-12-05
> $ find /boot/grub/stage1
(hd1,0)
$ root (hd1,0)
$ setup (hd1)
$ quit

When I start the machine it still says the NTloader is missing? I think it is because the computer still thinks to check the first drive for the NTloader. Your computer will probably be looking in your first hard drive's MBR for a pointer to a boot loader, (usually called the stage1 or IPL).
You just re-installed GRUB's IPL to your second hard disk's MBR, but your computer won't boot your second hard disk unless you [boot up from your BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").

Did you mean to install GRUB to your second hard disk insteat of your first one?
(It doesn't matter that the operating systems are both in your second hard disk, you can still boot them from the first hard disk's MBR).

Maybe you should try
```
$ find /boot/grub/stage1
 (hd1,0)
 $ root (hd1,0)
 $ setup (hd0)
 $ quit
```That will install GRUB in your MBR in your first hard disk.

---

### Post by Nathan Sweeney on 2008-12-06
> **morty35 said:**
> I have a desktop that has two hard drives.  The first is 14.7 GB and the second is 190 GB.  My computer was an XP only machine, but I got a virus.  
   I decided to switch to Linux primarily, but I have software that only runs on XP.  So I did a dual-boot.  I erased the first drive (which used to have XP operating system) because I wanted to install windows and XP on the second drive since it is much larger.
   I got the linux to work on the second drive (hd1,0) with no problems.  Afterward, I installed the Windows on a second partition on the second drive (hd1,1).  
   Now when I try to start the computer it says there is no NTloader.  I guess that was in the first harddrive and got deleted and when I installed windows it didn't create a new one.  
   I thought no biggie, it won't matter when I restore the grub boot loader.  I did the following commands to restore grub:

$ find /boot/grub/stage1
(hd1,0)
$ root (hd1,0)
$ setup (hd1)
$ quit

When I start the machine it still says the NTloader is missing?  I think it is because the computer still thinks to check the first drive for the NTloader.  

So how do I restore the grub loader so that I can use my computer without the loadup disk?

Here is the configuration:

hd0 - no operating system.  Just formatted NTFS and the location of my files in case the partitioning didn't work.  

hd1,0 Linux
hd1,1 XP

I think XP may have issues with being on the second hard disk.  What is the contents of /boot/grub/menu.lst?  You may have to use map in the menu.lst to convince XP that it is one the first hd.

```
map (hd0) (hd1)
map (hd1) (hd0)
```

---

### Post by morty35 on 2008-12-07
Thanks for the help.  Using setup (hd0) did the trick.  I still had problems with Windows being on the second drive, so I installed it on the first drive.  Both now work nicely.

---

