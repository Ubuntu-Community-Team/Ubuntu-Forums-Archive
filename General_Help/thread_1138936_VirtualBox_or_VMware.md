---
title: "VirtualBox or VMware?"
date: 2009-04-26
forum: General Help
---

### Post by DocEsq on 2009-04-26
Currently I dual boot XP/Ubuntu with Kubuntu on my computer.  I would like to run virtualization within Ubuntu and am wondering which is better and easier to install and work with.  

I would like to run XP within Ubuntu and maybe put the new version of Ubuntu in also for a test run. I would like one that would allow me to place the Virtual file onto another drive.

My system has a 2.0 Intel processor (no virtualization code on it) along with 2GB of RAM.

Any help would be appreciated.

Thanks.

---

### Post by doas777 on 2009-04-26
depends on whether you need games. I've always found that virtual box could not emulate directx driver extensions. other than that, virtualbox all the way, since it is open, and does the job.

vmware is a good product (at least better than the rest) but is encumbered. if that doesn't bother you, then i recommend vmware player. I have found that the vmware player bundled with a trial of vmware workstation runs my games better than the normal player install.

good luck

---

### Post by albinootje on 2009-04-26
> **DocEsq said:**
>  I would like to run XP within Ubuntu and maybe put the new version of Ubuntu in also for a test run. I would like one that would allow me to place the Virtual file onto another drive.

I really recommend trying VirtualBox over VMware in this case.
If you don't need usb and/or the virtual rdp, then use the 2.x OSE version from the Ubuntu repositories.

Otherwise go for the PUEL 2.2 version from the VirtualBox website : 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Use the VirtualBox repository, and install the packages "dkms" and "build-essential" for "seamless" VirtualBox usage after Linux kernel upgrades.

Afair the 2.1 and 2.2 versions do give your "host" network configuration option (very nice!), and usb should work out of the  
box.

---

