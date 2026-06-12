---
title: "Ndiswrapper modules"
date: 2006-03-02
forum: Desktop Environments
---

### Post by svenforum on 2006-03-02
How do I restore the ndiswrapper module?
Is something else going wrong? 

sven@flaptop:~$ sudo -s
root@flaptop:~# ndiswrapper -l
No drivers installed
root@flaptop:~# ndiswrapper -i bcmwl5/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@flaptop:~# ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@flaptop:~# depmod -a
root@flaptop:~# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
root@flaptop:~# /sbin/modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
root@flaptop:~# uname -r
2.6.12-10-386
root@flaptop:~#

---

### Post by swamytk on 2006-03-02
if you have recompiled your kernel, please ensure that either you have ndiswrapper selected to built into the kernel (so, need not to load through modprobe) or compiled as module (so, you can load through modprobe)

---

### Post by az on 2006-03-02
[QUOTE=svenforum]How do I restore the ndiswrapper module?

root@flaptop:~# uname -r
2.6.12-10-386
root@flaptop:~#[/QUOTE]


Did you try to compile it by hand?

No, you do not have to recompile your kernel!

sudo apt-get install --reinstall linux-image-2.6.12-10-386

There you do.  Also, install the ndiswrapper-utils package.  The utils must match the modules.  Remove any .inf drivers you have installed since the format they are stored in changed from one version of ndiswrapper to another.

Your broadcom chipset should work fine with the version of ndiswrapper that comes with Ubuntu on the install cd.

---

