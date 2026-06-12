---
title: "Failed to install the VMWare tools on Ubuntu virtual machine"
date: 2012-01-31
forum: Desktop Environments
---

### Post by lipzhong on 2012-01-31
Hi, expert,

I have latest ubuntu as a virtual machine on my windows 7 laptop using VMWare workstation.  My vmware workstation version is 7.1.5, the file name for the vmware tools is: VMwareTools-8.4.8-491717.tar.gz which seems a much higher version.

When I tried to install the vmware tools on the ubuntu virtual machine, I got quite some errors. The first error I got is:

/tmp/vmware-root/modules/vmhgfs-only/filesystem.c:69:26: error: ‘SPIN_LOCK_UNLOCKED’ undeclared here (not in a function)
make[2]: *** [/tmp/vmware-root/modules/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmhgfs-only'

From the error, it looks like the kernel for my ubuntu is 3.0.0-12.

However I did see the following line during compilation of VMWare tools:
Using 2.6.x kernel build system.


I did some search on internet, and I did find out that a lot of people are complaining about this. There are also some patches for this. However it seems that the patches would need to match the version of VMWare tools and I am getting really confused to what patch to apply. 

It would be appreciated that someone could give me a clear path on this. Thanks a lot in advance.

---

### Post by Raevyn on 2012-01-31
Hi

Sooo, are you saying that you are using VMWare Workstation version 7.1.5 but VMWare tools is using a version different? That doesnt make sense.. are you trying to install your own vmware tools or using the tools available in the program itself?

---

### Post by lipzhong on 2012-02-01
Thanks a lot of looking into this.

I am using the vmware tools available from the VMWare workstation. I am not sure how much attention people paid attention to the file name of vmware tools though. Maybe that it does have a different version track with vmware workstation. 

I guess with that, any idea what patch I should apply?

---

