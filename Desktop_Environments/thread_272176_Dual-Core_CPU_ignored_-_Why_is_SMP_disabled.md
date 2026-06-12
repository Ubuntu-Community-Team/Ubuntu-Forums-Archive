---
title: "Dual-Core CPU ignored - Why is SMP disabled?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by bughouse26 on 2006-10-05
Hi,

I installed ubuntu desktop 6.06 and it works except for the fact that it isn't using both of my cpus:

in dmesg:

....
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:6 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
.....

$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 2992.697
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm
bogomips        : 5990.25

Why doesn't the default kernel support SMP?

$ uname -a
Linux mbrown-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

How do I get an Ubuntu packaged smp kernel?

---

### Post by Albi on 2006-10-05
Try the 686 kernel

---

### Post by 5-HT on 2006-10-05
To grab a 686 kernel with SMP support and the appropriate restricted-modules package, you can install *linux-686 *via synaptic/apt/aptitude/etc..[I].
[/I]Once the new kernel is installed you can see if both cores are being recognized: cat /proc/cpuinfo.

---

### Post by [d3v] on 2006-10-23
I am having the same problem with a dual core Opteron. At work I am running a HT P4 no worries with SMP...

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64 GNU/Linux
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1804.115
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 3612.79
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

As you can see I am using the x64 SMP kernel. In dmesg it says that I do not have a multi-processor mobo :( 

```

[    0.000000] SMP: Allowing 2 CPUs, 2 hotplug CPUs

<snip>

[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 1804.115 MHz processor.

<snip>

[   36.244702] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.244705] CPU: L2 Cache: 1024K (64 bytes/line)
[   36.244708] CPU 0(2) -> Node 0 -> Core 0
[   36.244716] mtrr: v2.0 (20020519)
[   36.244724] SMP alternatives: switching to UP code
[   36.245126] checking if image is initramfs... it is
[   36.909437] Freeing initrd memory: 7604k freed
[   36.917870] ACPI: Looking for DSDT ... not found!
[   36.920488] ACPI: setting ELCR to 0200 (from 0c08)
[   36.921052] weird, boot CPU (#0) not listed by the BIOS.
[   36.921054] SMP motherboard not detected.


```

Anyone have any idea why this is happening? I am using an Asus A8R32-MVP Deluxe motherboard. ](*,)

---

### Post by jdong on 2006-10-23
Are your APIC/ACPI/SMP settings  enabled in your BIOS?

---

### Post by Aberrix on 2006-10-23
[Picking the Kernel thats Right for You]("http://www.ubuntuforums.org/showthread.php?t=85917")

---

