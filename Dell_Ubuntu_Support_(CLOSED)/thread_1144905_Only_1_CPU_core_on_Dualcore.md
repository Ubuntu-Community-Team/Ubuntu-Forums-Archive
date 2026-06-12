---
title: "Only 1 CPU core on Dualcore"
date: 2009-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LucidTaZ on 2009-05-01
Hello everyone,

I can only see one CPU core in my gnome-system-monitor. Also I notice my system is slower than an identical system where both cores are recognized. I have been reading [this]("http://ubuntuforums.org/archive/index.php/t-1062918.html") thread and got similar results on the executed commands. However, the fix (acpi=off) did not work for me.

I will show the outputs of some commands:

uname -a:
```
Linux taz-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

cat /proc/cpuinfo:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
stepping	: 2
cpu MHz		: 2000.201
cache size	: 2048 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4000.40
clflush size	: 64
power management:
```

mpstat -P ALL:
```
Linux 2.6.28-11-generic (taz-desktop) 	05/01/2009 	_i686_	(1 CPU)

12:30:31 PM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
12:30:31 PM  all   12.38    0.59    6.98    6.82    0.45    0.43    0.00    0.00   72.37
12:30:31 PM    0   12.38    0.59    6.98    6.82    0.45    0.43    0.00    0.00   72.37
```

dmesg | grep -i cpu:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004291] Initializing cgroup subsys cpuacct
[    0.004317] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004320] CPU: L2 cache: 2048K
[    0.004323] CPU: Physical Processor ID: 0
[    0.004325] CPU: Processor Core ID: 0
[    0.104457] weird, boot CPU (#0) not listedby the BIOS.
[    0.212366] Brought up 1 CPUs
[    0.212386] CPU0 attaching NULL sched-domain.
[    0.847445] cpufreq: No nForce2 chipset.
[    7.894894] cpuidle: using governor ladder
[    7.894895] cpuidle: using governor menu
```

sudo lshw -class cpu:
```
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       version: 6.15.2
       serial: 0000-06F2-0000-0000-0000-0000
       slot: Microprocessor
       size: 2GHz
       width: 64 bits
       clock: 800MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
```

Finally, my boot entry in lilo.conf:
```
image=/boot/vmlinuz-2.6.28-11-generic
        label="NA 2.6.28-11"
        append=" acpi=off noapic pci=nomsi pnpbios=off ro quiet splash"
        initrd=/boot/initrd.img-2.6.28-11-generic
        read-only
```

Please, who can help me? :)

---

### Post by LucidTaZ on 2009-05-01
I should add:
I use a Dell Optiplex 320i. All bios settings are good. (I checked them against my friend's bios where everything works fine)

---

### Post by LucidTaZ on 2009-05-01
I seem to have fixed this. This is what I did:

I changed my boot entry from
```
image=/boot/vmlinuz-2.6.28-11-generic
        label="Linux 2.6.28-11"
        append=" **acpi=off** **noapic** pci=nomsi pnpbios=off ro quiet splash"
        initrd=/boot/initrd.img-2.6.28-11-generic
        read-only
```

To
```
image=/boot/vmlinuz-2.6.28-11-generic
	label="Linux 2.6.28-11"
        append=" pci=nomsi pnpbios=off ro quiet splash"
        initrd=/boot/initrd.img-2.6.28-11-generic
        read-only
```

I don't really understand why it works, as I had to add "acpi=off" after the Jaunty upgrade to even make Ubuntu start properly. But right now my gnome-system-monitor shows two cpu's again!

---

### Post by yetihehe on 2009-12-02
I have triple core AMD Phenom and there is only one core after I added pci=nomsi (to try to eliminate random hanging, but looks like it's *just* xorg freeze)

---

