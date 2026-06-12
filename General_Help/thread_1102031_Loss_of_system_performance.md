---
title: "Loss of system performance"
date: 2009-03-21
forum: General Help
---

### Post by hultsfret on 2009-03-21
Hi,

I'm running xubuntu 8.10 on an 1,7GHz Thinkpad T41. The system used to run smooth all day. Since 2 days I'm experiencing a substational loss of system performance. Media playback ist impossible, internet browsing very slow and even while writing this text, the letters do lag in being displayed. 

I cannot image what this is due to, the only change I made to the system was installing the upgrades ubuntu proposed to me. It seems to me that the acpi package was updated, so maybe this is the issue.

/proc/cpuinfo shows normal behaviour (cpu clock scales from 600 to 1700MHz):

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips        : 1198.97
clflush size    : 64
power management:

"top" tells me that 95-98% of CPU is idle, so i suppose normal behaviour.

ps -aux gives out the following (running xterm and firefox): see attachment

I know I'm not supplying much information, but I greatly would appreciate any help. 

Regards,

Matthias

---

### Post by mikewhatever on 2009-03-21
How about the output of <df -h>. You could be running out of space on root or /home.

---

