---
title: "Virtualbox kubuntu 64b"
date: 2011-03-15
forum: Desktop Environments
---

### Post by runeh76 on 2011-03-15
Hi guys!

Founded little strange thing..
Tryed to install Kubuntu 10.10 64b to virtualbox.
Im running Ubuntu 10.10 32b.
I have 64b processor:
```
sudo lshw -c cpu
[sudo] password for user: 
  *-cpu:0                 
       description: CPU
       product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: 15.11.2
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 1800MHz
       capacity: 1800MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
  *-cpu:1
       physical id: 3
       bus info: cpu@1
       version: 15.11.2
       size: 1800MHz
       capacity: 1800MHz
       capabilities: cpufreq
```

Virtualbox says:
This kernel reguires an X86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel apprepriate for your CPU.

So it seems that virtualbox "read" OS bit, not CPU.

---

### Post by runeh76 on 2011-03-15
Founded setting in virtualbox, its working now  :)

PAE/NX  Enable

---

