---
title: "CPU Scaling problem on Desktop"
date: 2005-10-01
forum: Desktop Environments
---

### Post by casperlingus on 2005-10-01
I have a hunch this has to do with my 64-bit processor...

I have an AMD64 3000+ cpu with 1GB RAM, but I'm running 32-bit Ubuntu on it (because I was tired of trying to get everything to work in 64-bits).  I don't know if I was having this problem in the 64-bit version, but when *cat /proc/cpuinfo* I see that my CPU speed has been scaled down.  Here's the output:

[I]**casper@casper:~$ cat /proc/cpuinfo**
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 31
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 0
cpu MHz         : **1004.803**
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext lm 3dnowext 3dnow
bogomips        : **1988.83**[/I]

I did a ps aux | grep powernow to see that *powernowd* is running in the background.  I killed the process and the cat /proc/cpuinfo now outputs:

[I]**casper@casper:~$ cat /proc/cpuinfo**
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 31
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 0
cpu MHz         : **1808.646**
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext lm 3dnowext 3dnow
bogomips        : **3579.90**[/I]

Is there any particular reason why my computer was automatically configured to scale down the processor speed?  Is there any reason why I should leave it that way?  Or should I kill powernowd everytime I boot?

Casper...

---

### Post by eheintz on 2005-10-01
This is "working as intended". In short, the CPU will normally run at a lower speed and then be throttled upwards as load increases. How and when the CPU is throttled is configurable but I don't know the details off the top of my head. See the powernowd man pages for details.

The throttling is a "good thing" as it lowers power consumption and heat. I've found it can impact certain programs adversely when the CPU throttles while they are in use (particularly streaming audio) but your mileage may vary.

---

