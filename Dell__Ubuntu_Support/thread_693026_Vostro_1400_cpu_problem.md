---
title: "Vostro 1400 cpu problem"
date: 2008-02-10
forum: Dell  Ubuntu Support
---

### Post by jasonlfunk on 2008-02-10
I'm running Gutsy with Linux 2.6.22-14 on a Vostro 1400. It has a 1.6 ghz, core 2 duo. The issue is that it is only detecting 1 processor.

```

funkja@niniel:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz
stepping        : 13
cpu MHz         : 800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3195.90
clflush size    : 64

```

Any ideas why it isn't showing both cores?

---

### Post by faulkes on 2008-02-10
output of uname -a ?

Faulkes

---

### Post by jasonlfunk on 2008-02-10
Linux niniel 2.6.22-14-386 #1 Fri Feb 1 04:32:03 UTC 2008 i686 GNU/Linux

---

### Post by faulkes on 2008-02-10
> **jasonlfunk said:**
> Linux niniel 2.6.22-14-386 #1 Fri Feb 1 04:32:03 UTC 2008 i686 GNU/Linux

Would seem you aren't running an SMP kernel, which would be the reason it isn't showing the other core.

Easiest route would problably go into synaptic package manager and install the -generic kernel (rather than the -386).  I believe you can use the search term linux-image (and don't forget you may need to install the modules as well).

Faulkes

---

