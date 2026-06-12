---
title: "windows"
date: 2006-09-14
forum: Desktop Environments
---

### Post by checkeredshawn on 2006-09-14
I wanted to uninstall Ubuntu temporarily because I couldn't view the partition that it was installed on from Windows and for some reason that bothered me, so I read on some forum that I had to use the Windows CD to format the partition.  There was no option to format the partition so I figured I'd try to repair windows.  It went into the setup that looked like it was reformatting my entire hard drive so I shut down the computer in a panic.  Now, whenever the boot disk goes through it's very long set up, once it tells me that set up will resume at restart, it never works, and I think it might have something to do with grub because the CD expects the computer to boot right into Windows but in my case I have the choice of selecting Ubuntu or Windows.  When I do select Windows, though, it tells me that the setup will resume, but it just restarts my computer.  I can still access the files on my windows partition through Ubuntu, but I'd appreciate any advice in helping me fix Windows.

---

### Post by Lod on 2006-09-14
> **checkeredshawn said:**
> I wanted to uninstall Ubuntu temporarily because I couldn't view the partition that it was installed on from Windows and for some reason that bothered me, so I read on some forum that I had to use the Windows CD to format the partition.  There was no option to format the partition so I figured I'd try to repair windows.  It went into the setup that looked like it was reformatting my entire hard drive so I shut down the computer in a panic.  Now, whenever the boot disk goes through it's very long set up, once it tells me that set up will resume at restart, it never works, and I think it might have something to do with grub because the CD expects the computer to boot right into Windows but in my case I have the choice of selecting Ubuntu or Windows.  When I do select Windows, though, it tells me that the setup will resume, but it just restarts my computer.  I can still access the files on my windows partition through Ubuntu, but I'd appreciate any advice in helping me fix Windows.
For the future you can read linux partitions in Windows with [explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm).

For your current problem I'm not sure what you can do. Installing Windows after linux is a bad idea since the bootmanager of Windows will override your grub. And, oddly enough, Windows doens't handle dualboot very well. Especially when it concerns a non-Windows OS. ;) 

If it was me I would do the following:
First, backup the files I want to keep. Then reinstalling Windows (there is a basic partitioning tool in the setup) and then reinstall Ubuntu. If you weren't able to do partitioning in Windows you probably can do it during the Ubuntu installation.

---

### Post by raldz on 2006-09-14
To fix your MBR, boot into the Windows CD, then select Rescue.. when you are already in the command prompt, execute:

c:\> fixmbr

This should remove grub and you should be able to boot into Windows, but if it just reboots, then probably your Windows is in an unfinished installation state.. (can't do anything about that but reinstall Windows)

next, if you want to delete the Linux partition, download the GParted LiveCD:
[http://sourceforge.net/projects/gparted](http://sourceforge.net/projects/gparted)

---

### Post by UbuntuniX on 2006-09-14
The best way would be to use a partition manager such as GParted.

Or PartitionMagic for windows.

Anyway, come back!

---

