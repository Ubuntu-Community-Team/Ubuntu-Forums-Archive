---
title: "Bug has been fixed in upstream and ubuntu,but not in Debian Kernel"
date: 2020-06-13
forum: Debian
---

### Post by s10gopal on 2020-06-13
[B]A regression was introduced in 4.13-rc1(Mainline) and newer kernels. This regression caused battery drain during system suspend, hibernation or shutdown for some PCI devices that are not allowed by user space to wake up the system from sleep (or power off).

After Fix, Battery does not drain while running any ubuntu and upstream kernel,but does with debian kernel.The code that fixed the bug is also present in debian kernel source code.

Please provide suggestions. 
How ubuntu kernel is able to provide better battery backup than debian kernel? Is it possible to get information about the optimizations?


Bug has been reported.[Debian Bug Report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=962681") [Launchpad Bug Report]("https://bugs.launchpad.net/debian/+source/linux/+bug/1745646")



Thanks
[/B]

---

