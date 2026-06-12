---
title: "ACPI stucks for 20s on boot"
date: 2009-05-28
forum: General Help
---

### Post by Meextigrou on 2009-05-28
Hi,

I noticed that my kernel pauses for almost 20 seconds on load, with no hard drive activity.
Did anyone experience such behaviour ?

Here are my kernel logs, the kernel stucks after the message "..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1" : 

[    0.000000] Kernel command line: root=UUID=a7f0e3e7-ff25-47d8-948f-ccbabf5a5deb ro
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1599.990 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 4909440 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 952748k/981952k available (4126k kernel code, 28504k reserved, 220$
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency..$
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016763] SMP alternatives: switching to UP code
[    0.168023] ACPI: Core revision 20080926
[    0.171330] ACPI: Checking initramfs for custom DSDT
[    0.543624] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.591704] CPU0: AMD Sempron(tm) Processor LE-1150 stepping 01
[    0.592002] Brought up 1 CPUs
[    0.592002] Total of 1 processors activated (3199.98 BogoMIPS).
[    0.592002] CPU0 attaching NULL sched-domain.
[    0.592002] net_namespace: 776 bytes
[    0.592002] Booting paravirtualized kernel on bare hardware
[    0.592002] Time: 22:28:31  Date: 05/28/09
[    0.592002] regulator: core version 0.5
[    0.592002] NET: Registered protocol family 16
[    0.592002] EISA bus registered
[    0.592002] ACPI: bus type pci registered
[    0.592002] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.592002] PCI: MCFG area at f0000000 reserved in E820
[    0.592002] PCI: Using MMCONFIG for extended config space
[    0.592002] PCI: Using configuration type 1 for base access
[    0.592661] ACPI: EC: Look up EC in DSDT
[    0.603950] ACPI: Interpreter enabled
[    0.604008] ACPI: (supports S0 S3 S4 S5)
[    0.604268] ACPI: Using IOAPIC for interrupt routing
[    0.617342] ACPI: No dock devices found.


I tried "acpi=off" in the boot options, it does fix my issue but I still don't understand... what is that ?

---

### Post by Meextigrou on 2009-05-29
anybody ?

---

### Post by cottfcfan on 2009-06-28
Ive only just seen your post.
 Ive been having this problem since upgrading from 8.10. Tried reinstalling, same problem.
Ive googled the problem but cant find the answer.
Is anyone else having this problem?

---

