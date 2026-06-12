---
title: "Virtual machines with ACPI enabled keep freezing temporarily on a MacBook"
date: 2010-03-18
forum: Desktop Environments
---

### Post by jtayl22 on 2010-03-18
Virtual machines with ACPI enabled keep freezing temporarily on a MacBook

[http://www.virtualbox.org/ticket/2836](http://www.virtualbox.org/ticket/2836)


Host:

  # sudo dmidecode -s system-product-name
  MacBookPro5,2

  # cat /etc/lsb-release
  DISTRIB_ID=Ubuntu
  DISTRIB_RELEASE=9.10
  DISTRIB_CODENAME=karmic
  DISTRIB_DESCRIPTION="Ubuntu 9.10"

  # uname -a
  Linux mac 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

VirtualBox 3.1.4

Guest:
  Microsoft Windows XP Service Pack 3

Before:

  # time cat /proc/acpi/battery/*/*

  real 0m18.987s
  user 0m0.000s
  sys 0m0.020s

Reference:
  [http://bugzilla.kernel.org/show_bug.cgi?id=8246](http://bugzilla.kernel.org/show_bug.cgi?id=8246)

Change:

  # diff /etc/grub.d/10_linux /etc/grub.d/__10_linux.ORIG
  71c71
  <     linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} acpi=rsdp_forced ro $2
  ---
  >     linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2

  # update-grub

  # reboot


After:

  # time cat /proc/acpi/battery/*/*

  real    0m0.068s
  user    0m0.000s
  sys    0m0.010s

Now VirtualBox Guest is well behaved.

:!: :( #-o

Darn, VirtualBox was fine until I posted the "solved" message, and then it mocks me by falling back into the unusable behavior.

root@mac:~# time cat /proc/acpi/battery/*/*

real 0m**33**.552s 
user 0m0.000s 
sys 0m0.090s

---

### Post by jtayl22 on 2010-03-18
.

---

### Post by jtayl22 on 2010-04-01
Fixed in VirtualBox 3.1.6.

---

