---
title: "Kernel Update Broke boot"
date: 2009-04-17
forum: General Help
---

### Post by vertago1 on 2009-04-17
I have the jaunty beta running on a few machines, one took the kernel update to 2.6.28-11 fine but another one is now giving me:

Boot from (hd0,0) ext3 <UUID>

Error 2: Bad file or directory type

Press any key to continue...

When I try to boot from the old kernel the nvidia drivers will not load, but I can work from the console to some extent.

I checked the menu.lst file and the entries for the old and new kernel look identical.

I am going to try and run a fsck

---

### Post by vertago1 on 2009-04-17
I was able to fix the issue by removing the kernel module, cleaning the apt cache and reinstalling it.

---

