---
title: "Boot Error"
date: 2020-10-09
forum: Desktop Environments
---

### Post by whtemple1959 on 2020-10-09
Hello,

When I boot up my system I get this error ...
System program problem detected
Do you wish to report the problem now?

The problem I have is that there is no information on how to resolve this error.

Various information on my system is ...

$ uname -a
Linux pavilion
4.15.0-118-generic
#119-Ubuntu SMP Tue Sep 8 12:30:01 UTC 2020
x86_64
x86_64
x86_64
GNU/Linux

$ hardinfo
Computer
Processor    Intel(R) Core(TM)2 CPU 4300 @ 1.80GHz
Memory    3588MB (1681MB used)
Machine Type    Desktop
Operating System    Ubuntu 18.04.5 LTS
User Name    william (William H. Temple)
Date/Time    Fri 09 Oct 2020 12:51:27 PM EDT
Display
Resolution    1680x1050 pixels
OpenGL Renderer    AMD VERDE (DRM 2.50.0, 4.15.0-118-generic, LLVM 10.0.0)
X11 Vendor    The X.Org Foundation

Any help in resolving this issue will be greatly appreciated

Respectfully,
Bill

---

### Post by oldfred on 2020-10-09
Is error before grub menu? Perhaps then hardware.
If only Ubuntu you have to hold shift from BIOS until grub menu shows.
Looks like older BIOS only system. Are you running Ubuntu or lighter weight flavor?

Can you run live installer & then add Boot-Repair to see if boot issue.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

