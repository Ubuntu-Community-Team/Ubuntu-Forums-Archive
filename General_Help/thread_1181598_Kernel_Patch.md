---
title: "Kernel Patch"
date: 2009-06-08
forum: General Help
---

### Post by unmole on 2009-06-08
I am trying to apply a b43 injection patch (I am running jaunty,the patch is for kernel version 2.6.28 I get the following error message

root@ubuntu:/usr/src/linux-headers-2.6.28-11# patch -Np2 --dry-run --verbose -i b43-inj.patch
Hmm...  Looks like a unified diff to me...
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-2.6.28-rc3/drivers/net/wireless/b43/xmit.c.orig    2008-11-08 16:28:24.000000000 -0800
|+++ linux-2.6.28-rc3/drivers/net/wireless/b43/xmit.c    2008-11-08 16:13:31.000000000 -0800
--------------------------
File to patch: 

Do i have the correct version or am I doing something else wrong ?

---

### Post by unmole on 2009-06-08
Anyone?

---

