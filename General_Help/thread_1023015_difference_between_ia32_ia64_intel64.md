---
title: "difference between ia32 ia64 intel64"
date: 2008-12-27
forum: General Help
---

### Post by monkeyking on 2008-12-27
Hey,
Can someone elaborate on the diffence between ia32, ia64 intel64.
I know that the ia32 is 32bit arch but why is there 2 64 bit


my proc/cpuinfo is what should I use

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz
stepping        : 6
cpu MHz         : 2493.750
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov p
at pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_t
sc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr
dca sse4_1 lahf_lm
bogomips        : 4991.06
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:


```

thanks in advance

---

### Post by LoneWolfJack on 2008-12-27
first, there was AMD with their AMD64... then this took off so intel developed their version of the command set, calling it intel 64, emt64 and whatnot... basically, they're both the same, just from different companies.

---

