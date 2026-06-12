---
title: "Scilab JVM/libjava error"
date: 2012-08-25
forum: Education &amp; Science
---

### Post by kimothy1987 on 2012-08-25
Hi. I installed Scilab advaced client om my Ubuntu x86_64 box from the Ubuntu software center. The scilab-cli works great, but the gui scilab-adv-cli fails to load due to a JVM/libjava error.

```

Could not load JVM dynamic library (libjava).
Error: libjvm.so: cannot open shared object file: No such file or directory
If you are using a binary version of Scilab, please report a bug http://bugzilla.scilab.org/.
If you are using a self-built version of Scilab, update the script bin/scilab to provide the path to the JVM.
The problem might be related to SELinux. Try to deactivate it.
Please also check that you are not trying to run Scilab 64 bits on a 32 bits system (or vice versa).

Scilab cannot open JVM library.


```

I have disabled selinux as is recomended, but it don't help. Need scilab for my studies, so any help would be very appreciated!

---

### Post by j.behrendt on 2012-12-05
> **kimothy1987 said:**
> Hi. I installed Scilab advaced client om my Ubuntu x86_64 box from the Ubuntu software center. The scilab-cli works great, but the gui scilab-adv-cli fails to load due to a JVM/libjava error.

```

Could not load JVM dynamic library (libjava).
Error: libjvm.so: cannot open shared object file: No such file or directory
If you are using a binary version of Scilab, please report a bug http://bugzilla.scilab.org/.
If you are using a self-built version of Scilab, update the script bin/scilab to provide the path to the JVM.
The problem might be related to SELinux. Try to deactivate it.
Please also check that you are not trying to run Scilab 64 bits on a 32 bits system (or vice versa).

Scilab cannot open JVM library.


```

I have disabled selinux as is recomended, but it don't help. Need scilab for my studies, so any help would be very appreciated!

Update Scilab and install openjdk than it should run

---

