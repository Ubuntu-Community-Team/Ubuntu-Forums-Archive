---
title: "amd64 cpu speed question.."
date: 2006-01-28
forum: Desktop Environments
---

### Post by xxtommoxx on 2006-01-28
hey i just recently switched to ubuntu from windows... i have an amd 64 3500+ and windows reports it as 2.23 ghz.. when i do cat /proc/cpuinfo
 i get 1ghz or am i looking at the wrong info?

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 15
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 0
cpu MHz         : 1021.700
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 2018.21

```

---

### Post by debernardis on 2006-01-29
Likely your cpu is capable of reducing its clock to save energy and produce less heat (AMD cool'n'quiet).
Just try to do cat /proc/cpuinfo while your machine is doing something that asks power (on mine, it's enough to do apt-get update). You'll see many more megahertz!

---

