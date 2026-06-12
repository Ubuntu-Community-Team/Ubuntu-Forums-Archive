---
title: "Can't load 64bit kernel in VirtualBox OSE (with 64bit install)"
date: 2012-04-21
forum: Desktop Environments
---

### Post by Moozillaaa on 2012-04-21
Any ideas where to start here?

chucknb@chucknb-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : **AMD Athlon(tm) 64 X2 Dual Core Processor 6400+**
...
processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : **AMD Athlon(tm) 64 X2 Dual Core Processor 6400+**




chucknb@chucknb-desktop:~$ uname -m
**x86_64**
chucknb@chucknb-desktop:~$ 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216378&d=1334990765[/IMG]

---

### Post by drdos2006 on 2012-04-21
The only thing I could suggest is to download from here and start installation again. ( Removing the old installation first ).

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

regards

---

### Post by Moozillaaa on 2012-04-21
Thanks drdos...

I think I found the solution

**Q:** *Does VB support 64 bit guests?*
**A:** Support for 64 bit guests was introduced at version 2.0.0


looks like I have 1.5.6.

---

### Post by drdos2006 on 2012-04-21
Glad you found the problem.
It would help if you mark this thread as SOLVED as well.

regards

---

