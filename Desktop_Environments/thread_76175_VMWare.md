---
title: "VMWare"
date: 2005-10-14
forum: Desktop Environments
---

### Post by VR6Pete on 2005-10-14
I've always been a fan of Ubuntu, so decided to give it a test drive!

I liked it so much, I've decided to switch to it long-term, Everything "just worked" even the nvidia driver, without problem.

I'm trying to get VMWare installed, but im struggling with GCC versions. has anyone had first hand experience of installing the product under 5.10? Some advise needed.

Pete

---

### Post by nehalem on 2005-10-14
[http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

---

### Post by InsomniacUK on 2005-10-14
I've followed these instructions, but am getting this error during vmware-config.pl ....

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'

```

Then, when I try to actually run VMWare, it tells me it isn't correctly configured for my kernel and that I need to run vmware-config.pl again.

Can anyone help?

---

### Post by chaumurky on 2005-10-14
You need **vmware-any-any-update93** Untar it and run the script.

---

### Post by InsomniacUK on 2005-10-14
[QUOTE=chaumurky]You need **vmware-any-any-update93** Untar it and run the script.[/QUOTE]

I did, i'm still getting the above error. :(

**Scrap that. Thanks for the help, working now! :)**

---

### Post by VR6Pete on 2005-10-15
Thanking you kindly, VMWare now installed & working. keep up the good work Ubuntu!

---

