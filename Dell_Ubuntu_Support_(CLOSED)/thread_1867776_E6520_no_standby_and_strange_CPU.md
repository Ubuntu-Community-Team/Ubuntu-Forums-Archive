---
title: "E6520 no standby and strange CPU"
date: 2011-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DGTL_Magician on 2011-10-23
Hi,

Since I upgraded to 11.10 I can't put my computer in standby. It always switches back into screensaver.

Also my CPUInfo shows that I only have one CPU, instead of the quad-core with hyperthreading I actually have:

```
root@irulan:~# cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping	: 7
cpu MHz		: 1800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc up arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4390.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

So I suspect this is an ACPI issue. Any ideas?

---

