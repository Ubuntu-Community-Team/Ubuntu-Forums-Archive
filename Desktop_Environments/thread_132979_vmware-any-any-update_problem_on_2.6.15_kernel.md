---
title: "vmware-any-any-update problem on 2.6.15 kernel"
date: 2006-02-19
forum: Desktop Environments
---

### Post by blackwell on 2006-02-19
> 
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /usr/src/linux/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.15ck4'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
/bin/sh: scripts/genksyms/genksyms: Permission denied
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15ck4'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



i someone got any idea i will be grateful for tips

---

### Post by claes on 2006-02-19
I have stoped using vmware-any-any-update as the version of vmware I use handles the kernel drivers compile better. So try a newer version of vmware without vmware-any-any-update and see how that work.

Claes

---

### Post by blackwell on 2006-02-19
vmware-config.pl

generates this same problem :(

---

### Post by claes on 2006-02-19
[QUOTE=blackwell]vmware-config.pl

generates this same problem :([/QUOTE]

Which version of vmware are you using? I'm using vmware workstation 5.5.1 build-19175 without any problems in dapper with kernel 2.6.15-15.

Claes

---

### Post by blackwell on 2006-02-20
it was bad kernel souces in /usr/src/ problem 

now it works fine

thanx for your interest

---

### Post by joshuapurcell on 2006-03-01
These are the steps I did to solve the problem:
1)I edited the MAKEFILE.Kernel files using the instructions found here:
[http://clunixchit.blogspot.com/2006/02/vmware-player-and-livecd.html](http://clunixchit.blogspot.com/2006/02/vmware-player-and-livecd.html)
2)I applied the update98 vmware-any-any patch found here:
[http://ftp.cvut.cz/vmware/vmware-any-any-update98.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update98.tar.gz)
3)Re-ran vmware-config.pl and it worked.

I'm using kernel 2.6.15-ck4.

---

