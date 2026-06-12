---
title: "32 or 64 bit system"
date: 2009-05-22
forum: General Help
---

### Post by Nitewalker on 2009-05-22
I am using Ubuntu 9.04 and am not sure if I iinstalled the 32 or 64 bit system.  How can I check to see which one?

---

### Post by pro003 on 2009-05-22
you can run variations of 'uname' to get version & kernel information.

uname -r (kernel)
uname -a (everything), etc..

---

### Post by Nitewalker on 2009-05-22
*pro003...thanks from info, looks like I must be using the 64bit system.

nitewalker@smj:~$ uname -a
Linux smj 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
nitewalker@smj:~$

---

### Post by pro003 on 2009-05-22
in ma case where am using x32 version:

Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

and that must be x32, but am now on kubuntu, so don't take this for granted.

---

