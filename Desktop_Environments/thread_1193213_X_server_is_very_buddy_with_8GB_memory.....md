---
title: "X server is very buddy with 8GB memory...."
date: 2009-06-21
forum: Desktop Environments
---

### Post by carfield on 2009-06-21
I just upgrade my computer with 8GB memory, then x getting very unstable and easily crashed, I am using NVIDIA driver... is that related? However even after I change back to "vesa" driver the problem look like persist.... any idea for that? How can I check more? I just downgrade to 4GB in order to post this message

---

### Post by rt2002 on 2009-06-21
Did you run memtest to make sure the new RAM runs stable w the system first?  Are the RAM modules the same?

---

### Post by dazman19 on 2009-06-22
firstly run a memtest from the live cd. If you get errors it may be your ram. 

It may be that the ram you had is conflicting with the new ram. Sometimes they dont mix well. ?? could be a number of reasons...

If there are no errors there, I would re-compile the kernel headers for your nvidia driver, they may have been mismatched and compiled for your previous hardware configuration. 

from X save your work.. (if any)

1) <CTRL>+<ALT>+F3 (runlevel 3)
2) sudo /etc/init.d/gdm stop
3) sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run
4) sudo /etc/init.d/gdm start

good luck

---

### Post by carfield on 2009-06-22
> Did you run memtest to make sure the new RAM runs stable w the system first? Are the RAM modules the same?Yes, and it failed.... however, if I try individual 2 memory combination, it work fine, is that mean my motherboard have problem? I am using Asus P5KR

---

### Post by carfield on 2009-06-22
Will the problem easy caused by one of the memory is kingston, and the other are adata?

---

