---
title: "powernowd doesn't run"
date: 2006-08-16
forum: Desktop Environments
---

### Post by agrabah on 2006-08-16
Hello!

I'm having big troubles with cpu scaling as my laptop (a compaq nx9010) tends to overheat fast.

The installed powernowd daemon isn't running after boot (although it is supposed to), and I can't run it on my own. It gives me this output:

powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

[I]PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email][/I]

- I am running an appropriate kernel (Kubuntu Dapper)
- I do have something mounted on sys (I installed sysfs)
- lsmod tells me I have this modules with names similar to cpufreq:

[I]cpufreq_powersave       1920  0
cpufreq_stats           6688  0
cpufreq_userspace       6496  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
freq_table              4928  1 cpufreq_stats[/I]

and there does not seem to be a "cpufreq core" module anywhere around (at least none is printed when I do modprobe <bash-autocompletion>; only the loaded ones are shown.
- I have a pentium 4 2.6GHz, but when I do modprobe powernow <bash-autocompletion> I get only modules for amd k6, k7 and k8 modules.

Additionaly I find that some system services (found in system settings in kde) that seem to have something to do with power managment/cpu scaling  are not running (but they are marked to start at boot); these are cpufrequtils, acpid, laptop-mode.

I've googled around for the whole day and tried a plethora of things, but nothing worked.

Any ideas?

  Thanks

Tine

---

### Post by madchicken on 2006-08-28
Try modprobing acpi-cpufreq module. It shuold do the work (at least it did for me).

bye

---

### Post by agrabah on 2006-08-28
I already tried switching to acpi-cpufreq governor, but modprobe tells me:

```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.15-23-686/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

Any idea why?

Thanks,

Tine

---

### Post by agrabah on 2006-08-28
I completely forgot: I solved the issue with powernowd: I had to modprobe p4-clockmod module, and powernowd worked to some extent (I only had 2 cpu frequencies to choose from, because - at least I think - intel N60 errata); somehow the p4-clockmod module is patched so that available choices are limited).

Tine

---

