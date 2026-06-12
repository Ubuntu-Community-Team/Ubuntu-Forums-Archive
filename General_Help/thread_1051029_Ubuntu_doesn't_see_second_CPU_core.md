---
title: "Ubuntu doesn't see second CPU core"
date: 2009-01-26
forum: General Help
---

### Post by AntEater on 2009-01-26
For some reason Ubuntu does not see the second CPU core on my computer.  This machine has had both cpu cores working under Slackware without any problems.  Is there anything I need to do so that Ubuntu will see and use my second CPU core?

More detailed information below:

I'm running Ubuntu 8.10 (Intrepid), 32-bit.

Hardware: Shuttle XPC SD32G, Intel Core 2 1.8Ghz

my kernel:
> uname -a
Linux platypus 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

This is the stock kernel fetched via apt-get - no tweaks or recompiled anything.

The contents of /proc/cpuinfo:
> cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6320  @ 1.86GHz
stepping	: 6
cpu MHz		: 1867.000
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3734.34
clflush size	: 64
power management:

Finally, an excerpt from dmesg:

[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016513] SMP alternatives: switching to UP code
[    0.021799] Freeing SMP alternatives: 11k freed
[    0.021802] ACPI: Core revision 20080609
[    0.023318] ACPI: Checking initramfs for custom DSDT
[    0.392746] ACPI: setting ELCR to 0200 (from 8c20)
[    0.396073] weird, boot CPU (#0) not listedby the BIOS.
[    0.396077] SMP motherboard not detected.
[    0.400025] SMP disabled
[    0.400025] Brought up 1 CPUs
[    0.400025] Total of 1 processors activated (3734.34 BogoMIPS).
[    0.400025] CPU0 attaching sched-domain:
[    0.400025]  domain 0: span 0 level CPU
[    0.400025]   groups: 0

---

### Post by Xamiga on 2009-01-26
My Toshiba comes up with just 1 cpu when I boot with the nolapic kernel parm.

---

### Post by AntEater on 2009-02-13
> **Xamiga said:**
> My Toshiba comes up with just 1 cpu when I boot with the nolapic kernel parm.

That appears to be the only way I can boot this machine with any stability.  If I do not have the "noapic nolapic" appended to the kernel line at boot the system will hang hard.  the down side is that Ubuntu refuses to see the second cpu core with these boot parameters.  On the other hand, Slackware sees both cpus and is stable but I'd rather not spend all my time compiling the apps I want to use.

Is there no fix for this??

---

### Post by jonobr on 2009-02-13
I notice you are on breezy

I saw this for hardy and wonder does it relate.......?


[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498)

---

### Post by LowSky on 2009-02-13
Pay attention he said he is using Intrepid, not Breezy. He has only 5 post in 3 years, might explain why, he hasn't updated his profile.

Running noapic will only allow one processor to run, it is actually mentioned in any documentation you look up on the subject directly.

have you tried running an older kernel or even upgrading the BIOS?

---

