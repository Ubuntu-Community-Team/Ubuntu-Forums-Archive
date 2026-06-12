---
title: "ModelNet"
date: 2007-08-18
forum: Education &amp; Science
---

### Post by Rij on 2007-08-18
Greetings.
Has anyone installed ModelNet on Ubuntu cluster? I successfully ran configure. Now when I run make, I get the following:

Making all in linux_module
make[1]: Entering directory `/home/rij/modelnet/modelnet/linux/linux_module'
make -C /lib/modules/2.6.15-26-386/build M=/home/rij/modelnet/modelnet/linux/linux_module modules
make[2]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/rij/modelnet/modelnet/linux/linux_module'
make: *** [all-recursive] Error 1

---

### Post by max2k6 on 2007-10-04
Hi Rij,

I'm currently also trying to compile modelnet and I ran into the same problem. 
I have the linux headers installed in place, but this problem is still there.
Did you come to fix this problem?

Thank you very much,
max


> **Rij said:**
> Greetings.
Has anyone installed ModelNet on Ubuntu cluster? I successfully ran configure. Now when I run make, I get the following:

Making all in linux_module
make[1]: Entering directory `/home/rij/modelnet/modelnet/linux/linux_module'
make -C /lib/modules/2.6.15-26-386/build M=/home/rij/modelnet/modelnet/linux/linux_module modules
make[2]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/rij/modelnet/modelnet/linux/linux_module'
make: *** [all-recursive] Error 1

---

### Post by Rij on 2007-10-04
Unfortunately not. I had to use Debian instead. That worked.

---

