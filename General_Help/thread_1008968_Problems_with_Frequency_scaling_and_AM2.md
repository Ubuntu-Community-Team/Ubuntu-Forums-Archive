---
title: "Problems with Frequency scaling and AM2"
date: 2008-12-12
forum: General Help
---

### Post by wolfshark on 2008-12-12
Hi guys! I've never been so lucky to enable cpu frequency scaling, but today i decided to try one more time. My CPU is Athlon X2 3600+ and Asrock Alive NF6G motherboard. My problem is that i can't load the powernow-k8 module

sudo modprobe powernow-k8
> FATAL: Error inserting powernow_k8 (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device

I compiled my kernel - same thing. The bios is fine - C&Q is enabled and Asrock's 12% blabla booster is disabled. Actually in "/sys/devices/system/cpu/cpu0" there is no cpufreq folder at all. I will be very happy if somebody help me to diagnose the problem and maybe fixing it. Thanks!

Ubuntu 8.10


Edit: I tried to load powernow-k7 on my other pc with s.A Athlon processor and the result is the same. The Ubuntu installation is fresh.

---

