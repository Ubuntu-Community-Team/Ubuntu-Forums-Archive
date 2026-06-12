---
title: "T3500 Xenon Dual Core problem with shutdown and find Cores"
date: 2009-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bluepower on 2009-07-20
Hi,

I have the following problem with my Dell Dual Core T3500 xenon system. The problem is once the shutdown or reboot
by the system, here it goes not really down I only see system halt and by reboot the screen is black.
Furthermore, I do cat / proc / cpuinfo only one core of two Displayed. I currently use the 64bit Ubuntu 9.04
with the latest kernel is available. Do I need the kernel wich is optimized for xenon core 
so that the core is detected correctly? Furthermore, what can I change so that the PC shuts down by itself or
can restart without Ctrl + Alt + Del? During installation I had to turn off ACPI on, otherwise the installation
did not work. This I've after the installation enabled in the configuration.

Could anyone please help me with the problems.

---

### Post by devj on 2009-09-16
Hello all

I am experiencing similar problems on a Dell T3500 workstation we just purchased.  We are able to boot Ubuntu 9.04 with apci=off, but have not been able to have the second core picked up in /proc/cpuinfo.  We have tried adding an additional_cpus=1 argument to the boot line without success.  

It is running the 2.6.28-15-generic #49-Ubuntu SMP kernel.

Does anyone have any suggestions about other things I could try?

Thanks!

---

### Post by devj on 2009-10-05
SOLVED
I was able to get both processors recognized by doing the following:

In the BIOS setup I did "Load All Defaults"
I added acpi=ht as the only kernel boot parameter

---

