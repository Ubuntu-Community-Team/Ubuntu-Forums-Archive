---
title: "Finding out processor type"
date: 2005-12-14
forum: General Help
---

### Post by WebDrake on 2005-12-14
This is a bit of a weird question, but ....

... is there any Linux command that will let you know what the processor type is in a machine?  The situation is that I want to compile some code on a remote machine where I don't know the processor type, and I would like to optimize the code... ;-)

---

### Post by stuporglue on 2005-12-14
cat /proc/cpuinfo 

Should tell you everything Linux knows about your processor. Probably everything you want to know too.

---

### Post by Gandalf on 2005-12-14
yea it's easy just
```
cat /proc/cpuinfo
```
in terminal ;)

---

### Post by WebDrake on 2005-12-14
Many thanks! :-D

---

### Post by num1celticsfan on 2008-07-02
Can anyone tell me if the intel Intel Pentium dual-core E2160(1.8GHz) is 64 bit or 32 below I pasted the cpuid output

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 000006f2:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 15 - 
Extended model 0
Stepping 2
Reserved 0

Extended brand string: "Genuine Intel(R) CPU            2160  @ 1.80GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 2

Feature flags bfebfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
78: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0000-06F2-0000-0000-0000-0000


linux:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU            2160  @ 1.80GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3593.96
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU            2160  @ 1.80GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3591.03
clflush size	: 64

---

