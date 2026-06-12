---
title: "modprobe problem - FATAL: No such device"
date: 2008-12-13
forum: General Help
---

### Post by graysky on 2008-12-13
Running Intrepid on amd64.  I'm trying to get load a kernel module, but I get this someone cryptic error:

```
$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

I know the module is present; I can find it via a search.

```
$ locate acpi-cpu
/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
```

I'd be happy to post any log files etc. that would help diagnose this.

Thanks!

---

### Post by graysky on 2008-12-13
I figured this out finally.  See my post [here](http://ubuntuforums.org/showthread.php?p=6363028#post6363028) for the details.

---

