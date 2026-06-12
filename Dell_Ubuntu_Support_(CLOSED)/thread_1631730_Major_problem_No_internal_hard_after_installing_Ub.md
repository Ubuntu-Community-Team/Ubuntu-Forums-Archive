---
title: "Major problem No internal hard after installing Ubuntu 10.10"
date: 2010-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by elijante on 2010-11-27
Dear Ubuntu users and experts
 
Please I have a major problem in my Dell Inspiron 1545
 
After I installed Ubuntu 10.10 on external hard drive, the CD boot doen and the eject outside the drive. The problem is after the computer restarted Ubuntu had an error and didn't run. The diellama is I couldn't run my windows 7 again. when I restarted for many times, after it shows the dell logo, it gives me an error it says there is no device, 
" Error: No such device: a2b19fcd-d804-417a-ad6a-7a4707a1d7ca. 
grub rescue> "
 
I went to the bios setup and choose the internal hard as the primary boot and still the same problem. Please help I'm really panic I don't know wht to do this is my first time to deal with ubuntu. 
 
PS. I run ubuntu as trial from the CD and I found all my windows file and the internal hard still good. 
I'm waiting your answer. 
 
Help would be really appreciated
 
 
Foud the solution on Ubuntu forums. 
Thanx a lot to [[SIZE=5][COLOR=#000000]talsemgeest[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=397508")
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cnbiz850 on 2010-12-08
I think during your installation of Ubuntu, the disk partition numbers are changed.  You can boot Ubuntu from CD or USB flash, check the disk partitions, then access your Windows partition and change the in the file (boot.ini or something like that) accordingly.  Sorry I don't remember the exact solution.

---

