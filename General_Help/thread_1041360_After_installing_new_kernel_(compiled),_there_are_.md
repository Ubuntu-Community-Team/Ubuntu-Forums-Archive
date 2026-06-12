---
title: "After installing new kernel (compiled), there are no modules"
date: 2009-01-16
forum: General Help
---

### Post by paziek on 2009-01-16
Hello,

I'm on ubuntu 8.10
I have compiled kernel 2.6.28 from kernel.org - no patches - using **make all**.
Then I have used **make install** and it installed into /boot , but there are no modules in /lib/modules/ 
Whats wrong? Perhaps I should copy them manually, if so, then where do I find them? I'm pretty sure that I have compiled it with SOME modules, so there should be something in /lib/modules/ right?

---

### Post by x22 on 2009-01-16
youi need two more commands:
make modules
make modules_install

---

### Post by paziek on 2009-01-16
sweet, thanks :)

---

