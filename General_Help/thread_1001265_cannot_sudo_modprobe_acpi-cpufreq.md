---
title: "cannot sudo modprobe acpi-cpufreq"
date: 2008-12-03
forum: General Help
---

### Post by graysky on 2008-12-03
As a follow-up on my [post about cpu scaling](http://ubuntuforums.org/showthread.php?t=1000132) being non-functional on a fresh install of 8.10, I noticed that the [color=blue]acpi-cpufreq[/color] driver was active when running Debian/Lenny.  When I attempted to modprobe it under Intrepid, I got the following:

```
$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

I know it's present because:

```
$ locate acpi-cpu
/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
```

Can anyone offer advice for getting it loaded?  Hopefully, this will solve my problem in the referenced post.

Xeon quad-X3360
DFI LT P35-T2R motherboard
Intrepid x86_64

Thanks!

---

### Post by graysky on 2008-12-04
Not to bump my own thread, but after googling around for about an hour, I haven't found anything on this topic.  Could this be a bug with the kernel?

---

