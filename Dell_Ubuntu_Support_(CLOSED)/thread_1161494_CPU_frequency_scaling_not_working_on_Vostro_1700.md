---
title: "CPU frequency scaling not working on Vostro 1700"
date: 2009-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Loranga on 2009-05-16
It looks like the frequency scaling is not working on my Dell Vostro 1700 in Jaunty 9.04 (i386) (it worked in Intrepid 8.10). In my case, the frequency scaling seems to be stuck at 800MHz, while with 8.10 it could alter betweek 800MHz, 1.6GHz and "native" 2.2GHz.

I found it out when I tried to watch a film in HD quality and vlc went up to 105%. "CPU Frequency Scaling Monitor" says just 800MHz, and /proc/cpuinfo says 800MHz

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4389.12
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4388.96
clflush size	: 64
power management:
```

What to do about this?
Thanks for advice
Mats

---

### Post by orange_roughy on 2009-09-22
I've got the same problem with my Dell E6400 dual-core 2.27 GHz. It's running on A/C all the time. CPU cores are at 38 and 39 degrees Celsius (not very hot at all). Fan works fine.

STUCK AT 800 MHZ. I've tried all sorts of stuff suggested elsewhere in these forums; nothing helps.

---

