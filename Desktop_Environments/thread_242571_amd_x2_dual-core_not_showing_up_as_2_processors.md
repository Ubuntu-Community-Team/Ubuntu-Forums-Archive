---
title: "amd x2 dual-core not showing up as 2 processors"
date: 2006-08-23
forum: Desktop Environments
---

### Post by danny_mandel on 2006-08-23
Hi all, I installed Ubuntu for the first time last night and I am very impressed!  Things have gone incredibly smoothly and it is a wonderful introduction to the Debian way of doing things (I've been using RedHat/Fedora for the past 5 yrs).

Anyhow, I'm having problems getting my dual-core processor recognized by the kernel.  From other posts, I did find the name of the smp kernel and it is installed.  'uname -a' outputs the following:

[FONT="Courier New"]
Linux dmandel-desktop 2.6.15-26-amd64-k8 #1 SMP PREEMPT Thu Aug 3 03:11:38 UTC 2006 x86_64 GNU/Linux[/FONT]

But 'cat /proc/cpuinfo' outputs this:

[FONT="Courier New"]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2204.621
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4416.11
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
[/FONT]

I'm willing to dig deeper and try other avenues, but I'm not sure where to begin looking.  Any suggestions would be greatly appreciated.

Sincerely,
Danny Mandel

---

### Post by jackmacokc on 2006-08-23
i'm pretty sure smp is not supported under amd64. just update your kernel to k7, which includes k7-smp. its 32bit and so theres more support. unless you have a real need for 64bit at this point its not worth it.

---

### Post by RAOF on 2006-08-23
> **jackmacokc said:**
> i'm pretty sure smp is not supported under amd64. just update your kernel to k7, which includes k7-smp. its 32bit and so theres more support. unless you have a real need for 64bit at this point its not worth it.

That's just totally wrong.  SMP is definitely supported on AMD64 processors.  In fact, all the amd64 kernels are built with SMP support.  So the problem is obviously somewhere else...

I'm not sure what's wrong, but I'd suggest reposting this in the 64bit forum.  There are definitely people there with X2 processors showing as 2 cores - maybe they know what's wrong.

---

### Post by danny_mandel on 2006-08-24
Great, guys.  Thanks for the suggestions.  I've posted in the 64-bit topic and if that fails I guess I can always go back to 32-bit.

Sincerely,
Danny Mandel

---

### Post by codejunkie on 2006-08-24
i dont know if this will help, but my motherboard has a function in the bios that has to be enabled for dualcore support. it's worth a shot so check through the bios or the motherboard manual and see it yours has a setting like this that has to be enabled for dualcore support.

---

