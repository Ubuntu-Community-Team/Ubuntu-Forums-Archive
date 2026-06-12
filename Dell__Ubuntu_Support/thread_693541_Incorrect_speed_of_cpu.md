---
title: "Incorrect speed of cpu?"
date: 2008-02-11
forum: Dell  Ubuntu Support
---

### Post by 3molo on 2008-02-11
Hi,

/proc/cpuinfo shows wrong information. It claims cpu speed is 800mhz when it's 1.2 ghz. I have, to my knowledge, no frequency scaling or such. I do see "stepping 2", is this some form of cpu speed altering?

System is Dell D430 with U7600 1.2 ghz cpu, running Feisty.

Linux plopp 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
stepping        : 2
cpu MHz         : 800.000             <--- the problem
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 2394.05
clflush size    : 64


Any clues? Is it really running in 800 mhz or is this information not reliable?

Thanks in advance,

---

### Post by faulkes on 2008-02-11
Dell itself has stepping / cpufrequency stuff built into the bios iirc.

However, it is more likely that you have modules installed by default and aren't aware of them.

```

lsmod | grep cpu

```

Should show you any running cpufreq modules.

Faulkes

---

