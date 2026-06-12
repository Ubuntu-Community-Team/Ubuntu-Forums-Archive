---
title: "GParted generates an error when resize 2 TB disk"
date: 2013-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ruwan2 on 2013-06-07
Hi, I have a new Dell XPS 8500 desktop computer, which preinstalls Windows 8. I want to make this hard disk dual boot. The hard disk has already partitioned 6 partitions. I do not find one partition is an extension partition. The large partition is 1.81 TB, ntfb, primary partition. I suppose this is for Windows 8 installation. I try to resize this (1.81 TB) to make room for Linux with GParted, but it fails. An error dialogue box pops: "An error occurred while applying the operations. See the details for more information. IMPORTANT     If you want support, you need to provide the saved details!" Thus, I cannot continue to make this hard disk dual boot. What is the problem? Thanks,

---

### Post by oldfred on 2013-06-07
Windows 8 is always hibernated and you must turn that off. Some systems will have major boot issues if you do not turn it off and Linux will not modify a partition that is hibernated.

But you really need to modify the Windows NTFS partition with Windows disk tools and reboot a couple of times so it can run chkdsk and make whatever repairs it needs. Always best to separate that resize from the install so repairs to Windows work.

If new system you have UEFI and then gpt partitioning. With gpt you do not have primary, extended and logical partitions nor the 4 primary partition limit. You only have one type of partition and new limit is 128 partitions.
       
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


     WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
[http://www.eightforums.com/](http://www.eightforums.com/)

 
IF UEFI be sure to review link in my signature as there are a lot of issues, depending on vendor & model.
Additioinal users with 8500
 [SOLVED] Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices with info on UEFI settings
[http://ubuntuforums.org/showthread.php?t=2151494](http://ubuntuforums.org/showthread.php?t=2151494)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

