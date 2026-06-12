---
title: "Processor family for Intel 2080?"
date: 2009-01-01
forum: General Help
---

### Post by Masterofpsi on 2009-01-01
Hi, all.

I'm compiling a custom kernel because I need a higher system timer resolution in order to run [Rosegarden]("http://www.rosegardenmusic.com/"), and because my wireless card for some reason doesn't work with the [realtime kernel]("http://rt.wiki.kernel.org/index.php/Main_Page").

The problem is arising when I try to select my processor family. A sticker on my computer calls it an "intel Pentium Dual Core inside." Here are the contents of /proc/cpuinfo:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping	: 12
cpu MHz		: 800.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips	: 3466.73
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping	: 12
cpu MHz		: 800.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips	: 3467.08
clflush size	: 64
power management:

```

This topic was discussed in [this thread]("http://bbs.archlinux.org/viewtopic.php?id=59441"), and the processor there seems almost identical to mine, but they didn't quite reach a consensus.

---

### Post by Masterofpsi on 2009-01-01
No one?

---

### Post by Locutus_of_Borg on 2009-01-01
CPU Family: 6

Either "Pentium M" or "Newer Xeon"  i think....

---

