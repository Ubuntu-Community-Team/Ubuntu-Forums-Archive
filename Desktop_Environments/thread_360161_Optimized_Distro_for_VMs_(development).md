---
title: "Optimized Distro for VMs (development)"
date: 2007-02-12
forum: Desktop Environments
---

### Post by Thund3rstruck on 2007-02-12
Hi guys,

I'm seeking some advice. I have a laptop (2Ghz/2GB ram) for which I'm doing heavy programming on. The programming is C# for windows infrastructures. I have arrived at a situation where I have begun to rely heavily on virtualization. I'd like to use this opportunity to switch the host OS from Windows 2000 to Linux since, for best performance. the host OS should be as light as possible. The host OS will manage and initialize 6-8 windows workstation and server VMs (not simultaneously... of course). 

Can anyone tell me if Ubuntu is the optimum distro for hosting VMs? Or can anyone recommend a distro as easy as ubuntu to operate and manage but is small in size and leaves a small footprint on the machine?

Thanks,
T3

---

### Post by veloce on 2007-02-13
Hey, you're in the Ubuntu forums - how could anyone recommend anything but Ubuntu!

I'm using VMware server on top of ubuntu on a 1Gb core 2 duo ~1.6Mhz laptop.  Performance of windows vms is significantly better than when I had  windows as the base os.  I don't know why, but memory management is signifcantly better.  YMMV.

---

### Post by Datalanche on 2007-02-13
My machine is by no means top of the line(AMD Athlon XP 1.9GHz, 1GB RAM), but I use a virtual Windows 2000 machine in VMWare Server that is shared between my Kubuntu install and Windows XP Pro. The performance of the VM in Linux vs. Windows is VERY noticeable. It is much, much faster under Linux. I can't say how optimized Ubuntu is for virtual machines, but it worked just fine for me for general use.

---

