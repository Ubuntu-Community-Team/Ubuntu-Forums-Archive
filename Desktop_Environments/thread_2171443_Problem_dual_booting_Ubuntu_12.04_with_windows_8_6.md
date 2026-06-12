---
title: "Problem dual booting Ubuntu 12.04 with windows 8 64 bit."
date: 2013-08-30
forum: Desktop Environments
---

### Post by john66 on 2013-08-30
Hi guys!
A few days ago I tried to dual boot ubuntu with my windows 8 64 bit. It worked fine for 2 days and then Ubuntu didnt boot anymore and I had a lot of BSOD's in Windows 8(DPG_Wathcdog_Violation, Memory Mangement(also had memtest errors over 15000 in 5 mins), critical_service_failed). 
Im still afraid my ubuntu install screwed my windows installation. Do I need to worry for future problems(hardware,software)?
So I did a system restore and removed Ubuntu 12.04 64 bit from my PC. 
But I do want to use ubuntu so what did I do wrong? Or is it just my PC that cant handle ubuntu.
Specs
A10-5800k
1000gb HDD
8 GB ram
Windows 8 64 bit

---

### Post by oldfred on 2013-08-30
Is your system UEFI or BIOS? Pre-installed Windows 8 is always UEFI with gpt partitioning.

When dual booting the two systems should not interact. But do not attempt to write data into the Windows NTFS system partition as it always is hibernated. Best to turn off fast boot. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

