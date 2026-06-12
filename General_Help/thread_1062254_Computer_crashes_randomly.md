---
title: "Computer *crashes* randomly"
date: 2009-02-06
forum: General Help
---

### Post by Raskula on 2009-02-06
Ok First of all...

I have a...

Emachine EL1200-05w
Nvidia GeForce 6150SE Graphics
AMD Athlon 2650e Processor


When I'm using Ubuntu/Kubuntu, Sabayon, Fedora, any linux, it does this. In Windows it does not crash at all. 

What happens is the screen will randomly have like a background of white and a bunch of multi-colored lines all over it. (Like slashes) When I was using Fedora they could not figure out the problem. Hopfully they can figure it out here at Ubuntu so then I will be a permanent Ubuntu user. This problem only happens with my Desktop, my laptop does not do this.


I don't know how to post a log, so if a log would help, please tell me how to post one.


Lets have Ubuntu be the first one to fix this issue. Because all the other distros failed to help me.

I am not sure if this is a problem with the Nvidia driver or what.

Here is what Fedora did to help out, but it wasn't enough.

[http://forums.fedoraforum.org/showthread.php?t=209557](http://forums.fedoraforum.org/showthread.php?t=209557)



Anyway I switched to Ubuntu because gaming is really good for it and hopfully it will be the only distro that has this annoying problem fixed.

---

### Post by mjheagle8 on 2009-02-06
can you look through your logs to see if there are any errors that may have caused this?
logs can be accessed by system>administration>system log

---

### Post by Raskula on 2009-02-06
Ok here are the logs for Feb 6.

```
Feb  6 15:43:01 bryanc-desktop syslogd 1.5.0#2ubuntu6: restart.
Feb  6 15:43:01 bryanc-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Feb  6 15:43:01 bryanc-desktop kernel: Cannot find map file.
Feb  6 15:43:01 bryanc-desktop kernel: Loaded 66265 symbols from 83 modules.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] DMI 2.5 present.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] RAMDISK: 376fc000 - 37ecfa80
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: RSDT 37EE3000, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: SSDT 37EEA000, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: HPET 37EEA100, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: SLIC 37EEA140, 0176 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: MCFG 37EEA2C0, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] 894MB LOWMEM available.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #4 [00376fc000 - 0037ecfa80]          RAMDISK ==> [00376fc000 - 0037ecfa80]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Zone PFN ranges:
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Movable zone start PFN for each node
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Kernel command line: root=UUID=3636414a-c3ac-4751-8f21-2df79711b55f ro quiet splash 
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Initializing CPU#0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] TSC: using PIT calibration value
Feb  6 15:43:01 bryanc-desktop kernel: [    0.000000] Detected 1607.266 MHz processor.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] console [tty0] enabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Memory: 893704k/916352k available (2576k kernel code, 21976k reserved, 1165k data, 424k init, 0k highmem)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] virtual kernel memory layout:
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.53 BogoMIPS (lpj=6429064)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Security Framework initialized
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] using C1E aware idle routine
Feb  6 15:43:01 bryanc-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.016402] SMP alternatives: switching to UP code
Feb  6 15:43:01 bryanc-desktop kernel: [    0.022630] ACPI: Core revision 20080609
Feb  6 15:43:01 bryanc-desktop kernel: [    0.025301] ACPI: Checking initramfs for custom DSDT
Feb  6 15:43:01 bryanc-desktop kernel: [    0.448106] ENABLING IO-APIC IRQs
Feb  6 15:43:01 bryanc-desktop kernel: [    0.448339] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  6 15:43:01 bryanc-desktop kernel: [    0.489835] CPU0: AMD Athlon(tm) Processor 2650e stepping 02
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] Brought up 1 CPUs
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] Total of 1 processors activated (3214.53 BogoMIPS).
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] net_namespace: 840 bytes
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] Booting paravirtualized kernel on bare hardware
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] Time: 20:42:38  Date: 02/06/09
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] NET: Registered protocol family 16
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] EISA bus registered
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] ACPI: bus type pci registered
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] PCI: MCFG area at f0000000 reserved in E820
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] PCI: Using MMCONFIG for extended config space
Feb  6 15:43:01 bryanc-desktop kernel: [    0.492030] PCI: Using configuration type 1 for base access
Feb  6 15:43:01 bryanc-desktop kernel: [    0.503853] ACPI: Interpreter enabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.503858] ACPI: (supports S0 S3 S4 S5)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.503877] ACPI: Using IOAPIC for interrupt routing
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518556] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518824] pci 0000:00:01.1: PME# supported from D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518831] pci 0000:00:01.1: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518904] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518908] pci 0000:00:02.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518960] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.518965] pci 0000:00:02.1: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519047] pci 0000:00:05.0: PME# supported from D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519051] pci 0000:00:05.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519147] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519152] pci 0000:00:07.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519290] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519294] pci 0000:00:09.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519322] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519326] pci 0000:00:0b.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519352] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519356] pci 0000:00:0c.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519513] pci 0000:00:04.0: transparent bridge
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519645] pci 0000:03:00.0: PME# supported from D3hot D3cold
Feb  6 15:43:01 bryanc-desktop kernel: [    0.519649] pci 0000:03:00.0: PME# disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.595312] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.595582] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.595849] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.596124] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.596392] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.596664] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.596934] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.597204] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.597475] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.597742] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.598011] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.598280] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.598549] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.598823] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.599094] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.599363] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.599635] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.599905] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.600183] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.600527] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.600853] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.601188] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.601523] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.601858] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.602182] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.602506] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.602830] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.603154] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.603479] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.603804] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.604133] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.604457] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.604782] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.605106] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.605431] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.605757] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Feb  6 15:43:01 bryanc-desktop kernel: [    0.606083] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.606417] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Feb  6 15:43:01 bryanc-desktop kernel: [    0.606693] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  6 15:43:01 bryanc-desktop kernel: [    0.606734] pnp: PnP ACPI init
Feb  6 15:43:01 bryanc-desktop kernel: [    0.606743] ACPI: bus type pnp registered
Feb  6 15:43:01 bryanc-desktop kernel: [    0.614725] pnp: PnP ACPI: found 12 devices
Feb  6 15:43:01 bryanc-desktop kernel: [    0.614728] ACPI: ACPI bus type pnp unregistered
Feb  6 15:43:01 bryanc-desktop kernel: [    0.614733] PnPBIOS: Disabled by ACPI PNP
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615118] PCI: Using ACPI for IRQ routing
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NET: Registered protocol family 8
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NET: Registered protocol family 20
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NetLabel: Initializing
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NetLabel:  domain hash size = 128
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] NetLabel:  unlabeled traffic allowed by default
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Feb  6 15:43:01 bryanc-desktop kernel: [    0.615238] hpet0: 3 32-bit timers, 25000000 Hz
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617431] tracer: 772 pages allocated for 65536 entries of 48 bytes
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617434]    actual entries 65620
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617601] AppArmor: AppArmor Filesystem Enabled
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617631] ACPI: RTC can wake from S4
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1000-0x107f has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1080-0x10ff has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1400-0x147f has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1480-0x14ff has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1800-0x187f has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1880-0x18ff has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x2000-0x207f has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x2080-0x20ff has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:02: ioport range 0x295-0x314 has been reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653278] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653282] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653287] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653291] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653297] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653300] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653304] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653308] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653314] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653317] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653321] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653325] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653330] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653333] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653337] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653341] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653374] bus: 00 index 0 io port: [0, ffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653377] bus: 00 index 1 mmio: [0, ffffffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653380] bus: 01 index 0 io port: [b000, bfff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653383] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653386] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653388] bus: 01 index 3 io port: [0, ffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653391] bus: 01 index 4 mmio: [0, ffffffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653394] bus: 02 index 0 io port: [a000, afff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653397] bus: 02 index 1 mmio: [fde00000, fdefffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653399] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653402] bus: 02 index 3 mmio: [0, 0]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653405] bus: 03 index 0 io port: [9000, 9fff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653407] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653410] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653413] bus: 03 index 3 mmio: [0, 0]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653416] bus: 04 index 0 io port: [8000, 8fff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653418] bus: 04 index 1 mmio: [fda00000, fdafffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653421] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653424] bus: 04 index 3 mmio: [0, 0]
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653438] NET: Registered protocol family 2
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653623] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.653993] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.654874] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.655330] TCP: Hash tables configured (established 131072 bind 65536)
Feb  6 15:43:01 bryanc-desktop kernel: [    0.655334] TCP reno registered
Feb  6 15:43:01 bryanc-desktop kernel: [    0.655491] NET: Registered protocol family 1
Feb  6 15:43:01 bryanc-desktop kernel: [    0.655633] checking if image is initramfs... it is
Feb  6 15:43:01 bryanc-desktop kernel: [    1.519317] Freeing initrd memory: 8014k freed
Feb  6 15:43:01 bryanc-desktop kernel: [    1.520148] audit: initializing netlink socket (disabled)
Feb  6 15:43:01 bryanc-desktop kernel: [    1.520167] type=2000 audit(1233952958.520:1): initialized
Feb  6 15:43:01 bryanc-desktop kernel: [    1.527527] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530046] VFS: Disk quotas dquot_6.5.1
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530150] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530278] msgmni has been set to 1761
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530425] io scheduler noop registered
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530428] io scheduler anticipatory registered
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530431] io scheduler deadline registered
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530446] io scheduler cfq registered (default)
Feb  6 15:43:01 bryanc-desktop kernel: [    1.530483] pci 0000:00:00.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544058] pci 0000:00:04.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544076] pci 0000:00:05.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544106] pci 0000:00:07.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544122] pci 0000:00:08.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544138] pci 0000:00:08.1: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544155] pci 0000:00:09.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544172] pci 0000:00:0b.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544190] pci 0000:00:0c.0: Enabling HT MSI Mapping
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544361] pcieport-driver 0000:00:09.0: found MSI capability
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544542] pcieport-driver 0000:00:0b.0: found MSI capability
Feb  6 15:43:01 bryanc-desktop kernel: [    1.544705] pcieport-driver 0000:00:0c.0: found MSI capability
Feb  6 15:43:01 bryanc-desktop kernel: [    1.545071] isapnp: Scanning for PnP cards...
Feb  6 15:43:01 bryanc-desktop kernel: [    1.897766] isapnp: No Plug & Play device found
Feb  6 15:43:01 bryanc-desktop kernel: [    1.942630] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb  6 15:43:01 bryanc-desktop kernel: [    1.945424] brd: module loaded
Feb  6 15:43:01 bryanc-desktop kernel: [    1.945507] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Feb  6 15:43:01 bryanc-desktop kernel: [    1.945640] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946043] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946049] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946496] mice: PS/2 mouse device common for all mice
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946658] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946695] rtc0: alarms up to one year, y3k, hpet irqs
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946827] EISA: Probing bus 0 at eisa.0
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946835] Cannot allocate resource for EISA slot 1
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946839] Cannot allocate resource for EISA slot 2
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946855] Cannot allocate resource for EISA slot 8
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946857] EISA: Detected 0 cards.
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946861] cpuidle: using governor ladder
Feb  6 15:43:01 bryanc-desktop kernel: [    1.946864] cpuidle: using governor menu
Feb  6 15:43:01 bryanc-desktop kernel: [    1.947479] TCP cubic registered
Feb  6 15:43:01 bryanc-desktop kernel: [    1.947512] Using IPI No-Shortcut mode
Feb  6 15:43:01 bryanc-desktop kernel: [    1.947738] registered taskstats version 1
Feb  6 15:43:01 bryanc-desktop kernel: [    1.947897]   Magic number: 13:231:750
Feb  6 15:43:01 bryanc-desktop kernel: [    1.947909] tty ttyS1: hash matches
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948146] rtc_cmos 00:05: setting system clock to 2009-02-06 20:42:40 UTC (1233952960)
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948150] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948152] EDD information not available.
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948507] Freeing unused kernel memory: 424k freed
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948580] Write protecting the kernel text: 2580k
Feb  6 15:43:01 bryanc-desktop kernel: [    1.948624] Write protecting the kernel read-only data: 940k
Feb  6 15:43:01 bryanc-desktop kernel: [    1.968124] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Feb  6 15:43:01 bryanc-desktop kernel: [    2.216057] fuse init (API version 7.9)
Feb  6 15:43:01 bryanc-desktop kernel: [    2.255165] fan PNP0C0B:00: registered as cooling_device0
Feb  6 15:43:01 bryanc-desktop kernel: [    2.255174] ACPI: Fan [FAN] (on)
Feb  6 15:43:01 bryanc-desktop kernel: [    2.264788] processor ACPI0007:00: registered as cooling_device1
Feb  6 15:43:01 bryanc-desktop kernel: [    2.268116] thermal LNXTHERM:01: registered as thermal_zone0
Feb  6 15:43:01 bryanc-desktop kernel: [    2.268640] ACPI: Thermal Zone [THRM] (19 C)
Feb  6 15:43:01 bryanc-desktop kernel: [    3.516113] usbcore: registered new interface driver usbfs
Feb  6 15:43:01 bryanc-desktop kernel: [    3.516147] usbcore: registered new interface driver hub
Feb  6 15:43:01 bryanc-desktop kernel: [    3.530851] No dock devices found.
Feb  6 15:43:01 bryanc-desktop kernel: [    3.560081] usbcore: registered new device driver usb
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610058] SCSI subsystem initialized
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610726] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610739] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610757] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610816] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610847] ehci_hcd 0000:00:02.1: debug port 1
Feb  6 15:43:01 bryanc-desktop kernel: [    3.610869] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Feb  6 15:43:01 bryanc-desktop kernel: [    3.637094] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb  6 15:43:01 bryanc-desktop kernel: [    3.637303] usb usb1: configuration #1 chosen from 1 choice
Feb  6 15:43:01 bryanc-desktop kernel: [    3.637335] hub 1-0:1.0: USB hub found
Feb  6 15:43:01 bryanc-desktop kernel: [    3.637349] hub 1-0:1.0: 10 ports detected
Feb  6 15:43:01 bryanc-desktop kernel: [    3.844909] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Feb  6 15:43:01 bryanc-desktop kernel: [    3.844923] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Feb  6 15:43:01 bryanc-desktop kernel: [    3.844944] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb  6 15:43:01 bryanc-desktop kernel: [    3.844974] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Feb  6 15:43:01 bryanc-desktop kernel: [    3.845001] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Feb  6 15:43:01 bryanc-desktop kernel: [    3.903058] usb usb2: configuration #1 chosen from 1 choice
Feb  6 15:43:01 bryanc-desktop kernel: [    3.903094] hub 2-0:1.0: USB hub found
Feb  6 15:43:01 bryanc-desktop kernel: [    3.903108] hub 2-0:1.0: 10 ports detected
Feb  6 15:43:01 bryanc-desktop kernel: [    4.012129] usb 1-8: new high speed USB device using ehci_hcd and address 3
Feb  6 15:43:01 bryanc-desktop kernel: [    4.108503] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  6 15:43:01 bryanc-desktop kernel: [    4.109045] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Feb  6 15:43:01 bryanc-desktop kernel: [    4.109057] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
Feb  6 15:43:01 bryanc-desktop kernel: [    4.628800] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a6:b3:fd
Feb  6 15:43:01 bryanc-desktop kernel: [    4.628806] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629369] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629382] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629437] pata_acpi 0000:00:08.0: PCI INT A disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629943] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629947] pata_acpi 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.629977] pata_acpi 0000:00:08.1: PCI INT B disabled
Feb  6 15:43:01 bryanc-desktop kernel: [    4.651752] scsi0 : pata_amd
Feb  6 15:43:01 bryanc-desktop kernel: [    4.651879] scsi1 : pata_amd
Feb  6 15:43:01 bryanc-desktop kernel: [    4.652930] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb  6 15:43:01 bryanc-desktop kernel: [    4.652934] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb  6 15:43:01 bryanc-desktop kernel: [    4.699433] usb 1-8: configuration #1 chosen from 1 choice
Feb  6 15:43:01 bryanc-desktop kernel: [    4.819107] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.819217] scsi2 : sata_nv
Feb  6 15:43:01 bryanc-desktop kernel: [    4.819641] scsi3 : sata_nv
Feb  6 15:43:01 bryanc-desktop kernel: [    4.819898] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.819902] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Feb  6 15:43:01 bryanc-desktop kernel: [    4.876020] usb 2-7: new low speed USB device using ohci_hcd and address 2
Feb  6 15:43:01 bryanc-desktop kernel: [    5.091104] usb 2-7: configuration #1 chosen from 1 choice
Feb  6 15:43:01 bryanc-desktop kernel: [    5.100085] usbcore: registered new interface driver libusual
Feb  6 15:43:01 bryanc-desktop kernel: [    5.113101] Initializing USB Mass Storage driver...
Feb  6 15:43:01 bryanc-desktop kernel: [    5.126332] scsi4 : SCSI emulation for USB Mass Storage devices
Feb  6 15:43:01 bryanc-desktop kernel: [    5.127821] usbcore: registered new interface driver usb-storage
Feb  6 15:43:01 bryanc-desktop kernel: [    5.127828] USB Mass Storage support registered.
Feb  6 15:43:01 bryanc-desktop kernel: [    5.127958] usbcore: registered new interface driver hiddev
Feb  6 15:43:01 bryanc-desktop kernel: [    5.135609] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-7/2-7:1.0/input/input2
Feb  6 15:43:01 bryanc-desktop kernel: [    5.140142] input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:02.0-7
Feb  6 15:43:01 bryanc-desktop kernel: [    5.140170] usbcore: registered new interface driver usbhid
Feb  6 15:43:01 bryanc-desktop kernel: [    5.140174] usbhid: v2.6:USB HID core driver
Feb  6 15:43:01 bryanc-desktop kernel: [    5.596044] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  6 15:43:01 bryanc-desktop kernel: [    5.604313] ata4.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Feb  6 15:43:01 bryanc-desktop kernel: [    5.604317] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb  6 15:43:01 bryanc-desktop kernel: [    5.620309] ata4.00: configured for UDMA/133
Feb  6 15:43:01 bryanc-desktop kernel: [    5.620435] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Feb  6 15:43:01 bryanc-desktop kernel: [    5.621287] scsi 3:0:0:0: Attached scsi generic sg0 type 0
Feb  6 15:43:01 bryanc-desktop kernel: [    5.624804] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Feb  6 15:43:01 bryanc-desktop kernel: [    5.628975] scsi5 : sata_nv
Feb  6 15:43:01 bryanc-desktop kernel: [    5.629659] scsi6 : sata_nv
Feb  6 15:43:01 bryanc-desktop kernel: [    5.629930] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Feb  6 15:43:01 bryanc-desktop kernel: [    5.629934] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Feb  6 15:43:01 bryanc-desktop kernel: [    6.096041] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  6 15:43:01 bryanc-desktop kernel: [    6.104133] ata5.00: ATAPI: ATAPI   DVD A  DH16A6S, YA16, max UDMA/100
Feb  6 15:43:01 bryanc-desktop kernel: [    6.120142] ata5.00: configured for UDMA/100
Feb  6 15:43:01 bryanc-desktop kernel: [    6.433077] scsi 5:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6S   YA16 PQ: 0 ANSI: 5
Feb  6 15:43:01 bryanc-desktop kernel: [    6.433285] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Feb  6 15:43:01 bryanc-desktop kernel: [    6.468063] Driver 'sd' needs updating - please use bus_type methods
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470274] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470294] sd 3:0:0:0: [sda] Write Protect is off
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470325] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470406] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470421] sd 3:0:0:0: [sda] Write Protect is off
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470450] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  6 15:43:01 bryanc-desktop kernel: [    6.470455]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Feb  6 15:43:01 bryanc-desktop kernel: [    6.491538]  sda1 sda2 < sda5 >
Feb  6 15:43:01 bryanc-desktop kernel: [    6.516421] sd 3:0:0:0: [sda] Attached SCSI disk
Feb  6 15:43:01 bryanc-desktop kernel: [    6.530941] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Feb  6 15:43:01 bryanc-desktop kernel: [    6.530948] Uniform CD-ROM driver Revision: 3.20
Feb  6 15:43:01 bryanc-desktop kernel: [    6.710735] PM: Starting manual resume from disk
Feb  6 15:43:01 bryanc-desktop kernel: [    6.779219] kjournald starting.  Commit interval 5 seconds
Feb  6 15:43:01 bryanc-desktop kernel: [    6.779237] EXT3-fs: mounted filesystem with ordered data mode.
Feb  6 15:43:01 bryanc-desktop kernel: [   10.130551] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Feb  6 15:43:01 bryanc-desktop kernel: [   10.131746] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Feb  6 15:43:01 bryanc-desktop kernel: [   10.131905] sd 4:0:0:0: Attached scsi generic sg2 type 0
Feb  6 15:43:01 bryanc-desktop kernel: [   12.061989] udevd version 124 started
Feb  6 15:43:01 bryanc-desktop kernel: [   12.976764] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Feb  6 15:43:01 bryanc-desktop kernel: [   12.976816] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Feb  6 15:43:01 bryanc-desktop kernel: [   13.568292] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb  6 15:43:01 bryanc-desktop kernel: [   13.580048] ACPI: Power Button (FF) [PWRF]
Feb  6 15:43:01 bryanc-desktop kernel: [   13.580189] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Feb  6 15:43:01 bryanc-desktop kernel: [   13.596019] ACPI: Power Button (CM) [PWRB]
Feb  6 15:43:01 bryanc-desktop kernel: [   13.608262] ACPI: WMI: Mapper loaded
Feb  6 15:43:01 bryanc-desktop kernel: [   14.796806] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Feb  6 15:43:01 bryanc-desktop kernel: [   14.796814] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Feb  6 15:43:01 bryanc-desktop kernel: [   16.956181] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  6 15:43:01 bryanc-desktop kernel: [   16.992792] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  6 15:43:01 bryanc-desktop kernel: [   17.078123] Linux agpgart interface v0.103
Feb  6 15:43:01 bryanc-desktop kernel: [   17.292063] nvidia: module license 'NVIDIA' taints kernel.
Feb  6 15:43:01 bryanc-desktop kernel: [   17.659531] input: PC Speaker as /devices/platform/pcspkr/input/input5
Feb  6 15:43:01 bryanc-desktop kernel: [   17.737272] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Feb  6 15:43:01 bryanc-desktop kernel: [   17.737281] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Feb  6 15:43:01 bryanc-desktop kernel: [   17.740792] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
Feb  6 15:43:01 bryanc-desktop kernel: [   18.400208] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Feb  6 15:43:01 bryanc-desktop kernel: [   20.068370] lp: driver loaded but no devices found
Feb  6 15:43:01 bryanc-desktop kernel: [   20.327180] Adding 2642652k swap on /dev/sda5.  Priority:-1 extents:1 across:2642652k
Feb  6 15:43:01 bryanc-desktop kernel: [   20.898309] EXT3 FS on sda1, internal journal
Feb  6 15:43:01 bryanc-desktop kernel: [   21.946779] type=1505 audit(1233952980.016:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4110
Feb  6 15:43:01 bryanc-desktop kernel: [   22.206753] type=1505 audit(1233952980.276:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4115
Feb  6 15:43:01 bryanc-desktop kernel: [   22.207050] type=1505 audit(1233952980.276:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4115
Feb  6 15:43:01 bryanc-desktop kernel: [   22.351252] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb  6 15:43:01 bryanc-desktop kernel: [   23.264653] powernow-k8: Found 1 AMD Athlon(tm) Processor 2650e processors (1 cpu cores) (version 2.20.00)
Feb  6 15:43:01 bryanc-desktop kernel: [   23.264693] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16
Feb  6 15:43:01 bryanc-desktop kernel: [   23.264696] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
Feb  6 15:43:02 bryanc-desktop kernel: [   24.028057] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb  6 15:43:02 bryanc-desktop kernel: [   24.087088] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb  6 15:43:02 bryanc-desktop kernel: [   24.087095] apm: overridden by ACPI.
Feb  6 15:43:02 bryanc-desktop kernel: [   24.268516] ppdev: user-space parallel port driver
Feb  6 15:43:04 bryanc-desktop kernel: [   26.049396] Bluetooth: Core ver 2.13
Feb  6 15:43:04 bryanc-desktop kernel: [   26.052356] NET: Registered protocol family 31
Feb  6 15:43:04 bryanc-desktop kernel: [   26.052362] Bluetooth: HCI device and connection manager initialized
Feb  6 15:43:04 bryanc-desktop kernel: [   26.052366] Bluetooth: HCI socket layer initialized
Feb  6 15:43:04 bryanc-desktop kernel: [   26.084025] Bluetooth: L2CAP ver 2.11
Feb  6 15:43:04 bryanc-desktop kernel: [   26.084031] Bluetooth: L2CAP socket layer initialized
Feb  6 15:43:04 bryanc-desktop kernel: [   26.134204] Bluetooth: RFCOMM socket layer initialized
Feb  6 15:43:04 bryanc-desktop kernel: [   26.134504] Bluetooth: RFCOMM TTY layer initialized
Feb  6 15:43:04 bryanc-desktop kernel: [   26.134509] Bluetooth: RFCOMM ver 1.10
Feb  6 15:43:04 bryanc-desktop kernel: [   26.134916] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  6 15:43:04 bryanc-desktop kernel: [   26.134920] Bluetooth: BNEP filters: protocol multicast
Feb  6 15:43:04 bryanc-desktop kernel: [   26.188657] Bridge firewalling registered
Feb  6 15:43:04 bryanc-desktop kernel: [   26.213530] Bluetooth: SCO (Voice Link) ver 0.6
Feb  6 15:43:04 bryanc-desktop kernel: [   26.213537] Bluetooth: SCO socket layer initialized
Feb  6 15:43:06 bryanc-desktop kernel: [   28.000035] Clocksource tsc unstable (delta = -213349348 ns)
Feb  6 15:43:08 bryanc-desktop kernel: [   30.472109] NET: Registered protocol family 17
Feb  6 15:43:12 bryanc-desktop kernel: [   34.736321] NET: Registered protocol family 10
Feb  6 15:43:12 bryanc-desktop kernel: [   34.738725] lo: Disabled Privacy Extensions
Feb  6 15:43:17 bryanc-desktop pulseaudio[5503]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  6 15:43:17 bryanc-desktop pulseaudio[5505]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  6 15:43:17 bryanc-desktop pulseaudio[5505]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  6 15:47:19 bryanc-desktop kernel: [  282.941241] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Feb  6 15:47:21 bryanc-desktop kernel: [  284.515311] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Feb  6 16:03:00 bryanc-desktop -- MARK --
Feb  6 16:12:51 bryanc-desktop syslogd 1.5.0#2ubuntu6: restart.
Feb  6 16:23:00 bryanc-desktop -- MARK --
Feb  6 16:43:00 bryanc-desktop -- MARK --
Feb  6 17:03:00 bryanc-desktop -- MARK --
Feb  6 17:22:18 bryanc-desktop syslogd 1.5.0#2ubuntu6: restart.
Feb  6 17:22:18 bryanc-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Feb  6 17:22:18 bryanc-desktop kernel: Cannot find map file.
Feb  6 17:22:18 bryanc-desktop kernel: Loaded 66265 symbols from 83 modules.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] DMI 2.5 present.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] RAMDISK: 376fc000 - 37ecfa80
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: RSDT 37EE3000, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: SSDT 37EEA000, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: HPET 37EEA100, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: SLIC 37EEA140, 0176 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: MCFG 37EEA2C0, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] 894MB LOWMEM available.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #4 [00376fc000 - 0037ecfa80]          RAMDISK ==> [00376fc000 - 0037ecfa80]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Zone PFN ranges:
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Movable zone start PFN for each node
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Kernel command line: root=UUID=3636414a-c3ac-4751-8f21-2df79711b55f ro quiet splash 
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Initializing CPU#0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] TSC: using PIT calibration value
Feb  6 17:22:18 bryanc-desktop kernel: [    0.000000] Detected 1607.268 MHz processor.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] console [tty0] enabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Memory: 893704k/916352k available (2576k kernel code, 21976k reserved, 1165k data, 424k init, 0k highmem)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] virtual kernel memory layout:
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.53 BogoMIPS (lpj=6429072)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Security Framework initialized
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] using C1E aware idle routine
Feb  6 17:22:18 bryanc-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.016402] SMP alternatives: switching to UP code
Feb  6 17:22:18 bryanc-desktop kernel: [    0.022626] ACPI: Core revision 20080609
Feb  6 17:22:18 bryanc-desktop kernel: [    0.025296] ACPI: Checking initramfs for custom DSDT
Feb  6 17:22:18 bryanc-desktop kernel: [    0.448096] ENABLING IO-APIC IRQs
Feb  6 17:22:18 bryanc-desktop kernel: [    0.448331] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  6 17:22:18 bryanc-desktop kernel: [    0.489180] CPU0: AMD Athlon(tm) Processor 2650e stepping 02
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] Brought up 1 CPUs
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] Total of 1 processors activated (3214.53 BogoMIPS).
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] net_namespace: 840 bytes
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] Booting paravirtualized kernel on bare hardware
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] Time: 22:21:53  Date: 02/06/09
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] NET: Registered protocol family 16
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] EISA bus registered
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] ACPI: bus type pci registered
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] PCI: MCFG area at f0000000 reserved in E820
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] PCI: Using MMCONFIG for extended config space
Feb  6 17:22:18 bryanc-desktop kernel: [    0.492030] PCI: Using configuration type 1 for base access
Feb  6 17:22:18 bryanc-desktop kernel: [    0.503850] ACPI: Interpreter enabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.503855] ACPI: (supports S0 S3 S4 S5)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.503874] ACPI: Using IOAPIC for interrupt routing
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518553] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518822] pci 0000:00:01.1: PME# supported from D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518828] pci 0000:00:01.1: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518902] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518906] pci 0000:00:02.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518958] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.518962] pci 0000:00:02.1: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519045] pci 0000:00:05.0: PME# supported from D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519049] pci 0000:00:05.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519146] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519151] pci 0000:00:07.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519289] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519293] pci 0000:00:09.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519321] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519324] pci 0000:00:0b.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519351] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519355] pci 0000:00:0c.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519510] pci 0000:00:04.0: transparent bridge
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519642] pci 0000:03:00.0: PME# supported from D3hot D3cold
Feb  6 17:22:18 bryanc-desktop kernel: [    0.519646] pci 0000:03:00.0: PME# disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.595303] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.595573] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.595841] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.596116] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.596385] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.596657] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.596927] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.597199] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.597470] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.597737] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.598007] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.598277] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.598547] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.598821] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.599092] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.599362] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.599634] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.599905] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.600183] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.600528] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.600854] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.601189] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.601525] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.601860] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.602185] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.602509] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.602834] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.603158] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.603484] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.603810] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.604139] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.604465] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.604790] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.605115] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.605441] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.605767] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Feb  6 17:22:18 bryanc-desktop kernel: [    0.606093] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.606428] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Feb  6 17:22:18 bryanc-desktop kernel: [    0.606704] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  6 17:22:18 bryanc-desktop kernel: [    0.606744] pnp: PnP ACPI init
Feb  6 17:22:18 bryanc-desktop kernel: [    0.606753] ACPI: bus type pnp registered
Feb  6 17:22:18 bryanc-desktop kernel: [    0.614743] pnp: PnP ACPI: found 12 devices
Feb  6 17:22:18 bryanc-desktop kernel: [    0.614747] ACPI: ACPI bus type pnp unregistered
Feb  6 17:22:18 bryanc-desktop kernel: [    0.614751] PnPBIOS: Disabled by ACPI PNP
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615134] PCI: Using ACPI for IRQ routing
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NET: Registered protocol family 8
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NET: Registered protocol family 20
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NetLabel: Initializing
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NetLabel:  domain hash size = 128
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] NetLabel:  unlabeled traffic allowed by default
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Feb  6 17:22:18 bryanc-desktop kernel: [    0.615254] hpet0: 3 32-bit timers, 25000000 Hz
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617431] tracer: 772 pages allocated for 65536 entries of 48 bytes
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617434]    actual entries 65620
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617600] AppArmor: AppArmor Filesystem Enabled
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617630] ACPI: RTC can wake from S4
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1000-0x107f has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1080-0x10ff has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1400-0x147f has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1480-0x14ff has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1800-0x187f has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x1880-0x18ff has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x2000-0x207f has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:01: ioport range 0x2080-0x20ff has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:02: ioport range 0x295-0x314 has been reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.617640] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653292] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653296] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653302] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653306] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653312] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653315] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653319] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653323] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653328] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653331] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653335] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653339] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653344] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653347] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653351] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653355] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653389] bus: 00 index 0 io port: [0, ffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653392] bus: 00 index 1 mmio: [0, ffffffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653395] bus: 01 index 0 io port: [b000, bfff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653397] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653400] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653403] bus: 01 index 3 io port: [0, ffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653406] bus: 01 index 4 mmio: [0, ffffffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653408] bus: 02 index 0 io port: [a000, afff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653411] bus: 02 index 1 mmio: [fde00000, fdefffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653414] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653417] bus: 02 index 3 mmio: [0, 0]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653419] bus: 03 index 0 io port: [9000, 9fff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653422] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653425] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653427] bus: 03 index 3 mmio: [0, 0]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653430] bus: 04 index 0 io port: [8000, 8fff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653433] bus: 04 index 1 mmio: [fda00000, fdafffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653436] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653438] bus: 04 index 3 mmio: [0, 0]
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653452] NET: Registered protocol family 2
Feb  6 17:22:18 bryanc-desktop kernel: [    0.653639] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.654014] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.654894] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.655351] TCP: Hash tables configured (established 131072 bind 65536)
Feb  6 17:22:18 bryanc-desktop kernel: [    0.655355] TCP reno registered
Feb  6 17:22:18 bryanc-desktop kernel: [    0.655512] NET: Registered protocol family 1
Feb  6 17:22:18 bryanc-desktop kernel: [    0.655654] checking if image is initramfs... it is
Feb  6 17:22:18 bryanc-desktop kernel: [    1.519344] Freeing initrd memory: 8014k freed
Feb  6 17:22:18 bryanc-desktop kernel: [    1.520176] audit: initializing netlink socket (disabled)
Feb  6 17:22:18 bryanc-desktop kernel: [    1.520195] type=2000 audit(1233958913.520:1): initialized
Feb  6 17:22:18 bryanc-desktop kernel: [    1.527556] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530074] VFS: Disk quotas dquot_6.5.1
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530178] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530306] msgmni has been set to 1761
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530454] io scheduler noop registered
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530457] io scheduler anticipatory registered
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530460] io scheduler deadline registered
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530474] io scheduler cfq registered (default)
Feb  6 17:22:18 bryanc-desktop kernel: [    1.530511] pci 0000:00:00.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544058] pci 0000:00:04.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544076] pci 0000:00:05.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544106] pci 0000:00:07.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544122] pci 0000:00:08.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544138] pci 0000:00:08.1: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544155] pci 0000:00:09.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544172] pci 0000:00:0b.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544190] pci 0000:00:0c.0: Enabling HT MSI Mapping
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544361] pcieport-driver 0000:00:09.0: found MSI capability
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544543] pcieport-driver 0000:00:0b.0: found MSI capability
Feb  6 17:22:18 bryanc-desktop kernel: [    1.544707] pcieport-driver 0000:00:0c.0: found MSI capability
Feb  6 17:22:18 bryanc-desktop kernel: [    1.545073] isapnp: Scanning for PnP cards...
Feb  6 17:22:18 bryanc-desktop kernel: [    1.897786] isapnp: No Plug & Play device found
Feb  6 17:22:18 bryanc-desktop kernel: [    1.942585] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb  6 17:22:18 bryanc-desktop kernel: [    1.945391] brd: module loaded
Feb  6 17:22:18 bryanc-desktop kernel: [    1.945473] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Feb  6 17:22:18 bryanc-desktop kernel: [    1.945608] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946009] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946015] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946459] mice: PS/2 mouse device common for all mice
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946624] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946660] rtc0: alarms up to one year, y3k, hpet irqs
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946795] EISA: Probing bus 0 at eisa.0
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946802] Cannot allocate resource for EISA slot 1
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946806] Cannot allocate resource for EISA slot 2
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946822] Cannot allocate resource for EISA slot 8
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946824] EISA: Detected 0 cards.
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946830] cpuidle: using governor ladder
Feb  6 17:22:18 bryanc-desktop kernel: [    1.946832] cpuidle: using governor menu
Feb  6 17:22:18 bryanc-desktop kernel: [    1.947449] TCP cubic registered
Feb  6 17:22:18 bryanc-desktop kernel: [    1.947482] Using IPI No-Shortcut mode
Feb  6 17:22:18 bryanc-desktop kernel: [    1.947708] registered taskstats version 1
Feb  6 17:22:18 bryanc-desktop kernel: [    1.947869]   Magic number: 13:581:400
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948117] rtc_cmos 00:05: setting system clock to 2009-02-06 22:21:55 UTC (1233958915)
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948122] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948124] EDD information not available.
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948478] Freeing unused kernel memory: 424k freed
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948551] Write protecting the kernel text: 2580k
Feb  6 17:22:18 bryanc-desktop kernel: [    1.948596] Write protecting the kernel read-only data: 940k
Feb  6 17:22:18 bryanc-desktop kernel: [    1.968193] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Feb  6 17:22:18 bryanc-desktop kernel: [    2.216056] fuse init (API version 7.9)
Feb  6 17:22:18 bryanc-desktop kernel: [    2.257697] fan PNP0C0B:00: registered as cooling_device0
Feb  6 17:22:18 bryanc-desktop kernel: [    2.257706] ACPI: Fan [FAN] (on)
Feb  6 17:22:18 bryanc-desktop kernel: [    2.267137] processor ACPI0007:00: registered as cooling_device1
Feb  6 17:22:18 bryanc-desktop kernel: [    2.270444] thermal LNXTHERM:01: registered as thermal_zone0
Feb  6 17:22:18 bryanc-desktop kernel: [    2.270969] ACPI: Thermal Zone [THRM] (31 C)
Feb  6 17:22:18 bryanc-desktop kernel: [    3.528104] usbcore: registered new interface driver usbfs
Feb  6 17:22:18 bryanc-desktop kernel: [    3.528138] usbcore: registered new interface driver hub
Feb  6 17:22:18 bryanc-desktop kernel: [    3.545197] No dock devices found.
Feb  6 17:22:18 bryanc-desktop kernel: [    3.576077] usbcore: registered new device driver usb
Feb  6 17:22:18 bryanc-desktop kernel: [    3.604951] SCSI subsystem initialized
Feb  6 17:22:18 bryanc-desktop kernel: [    3.605062] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  6 17:22:18 bryanc-desktop kernel: [    3.605624] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Feb  6 17:22:18 bryanc-desktop kernel: [    3.605637] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125199] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a6:b3:fd
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125206] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125810] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125822] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125843] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125894] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Feb  6 17:22:18 bryanc-desktop kernel: [    4.125921] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Feb  6 17:22:18 bryanc-desktop kernel: [    4.182210] usb usb1: configuration #1 chosen from 1 choice
Feb  6 17:22:18 bryanc-desktop kernel: [    4.182250] hub 1-0:1.0: USB hub found
Feb  6 17:22:18 bryanc-desktop kernel: [    4.182264] hub 1-0:1.0: 10 ports detected
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388826] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388839] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388859] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388889] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388921] ehci_hcd 0000:00:02.1: debug port 1
Feb  6 17:22:18 bryanc-desktop kernel: [    4.388947] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Feb  6 17:22:18 bryanc-desktop kernel: [    4.400026] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb  6 17:22:18 bryanc-desktop kernel: [    4.400224] usb usb2: configuration #1 chosen from 1 choice
Feb  6 17:22:18 bryanc-desktop kernel: [    4.400257] hub 2-0:1.0: USB hub found
Feb  6 17:22:18 bryanc-desktop kernel: [    4.400268] hub 2-0:1.0: 10 ports detected
Feb  6 17:22:18 bryanc-desktop kernel: [    4.609908] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.609924] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.609982] pata_acpi 0000:00:08.0: PCI INT A disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    4.610482] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.610486] pata_acpi 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.610515] pata_acpi 0000:00:08.1: PCI INT B disabled
Feb  6 17:22:18 bryanc-desktop kernel: [    4.624033] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.631491] scsi0 : sata_nv
Feb  6 17:22:18 bryanc-desktop kernel: [    4.632826] scsi1 : sata_nv
Feb  6 17:22:18 bryanc-desktop kernel: [    4.633076] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.633080] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Feb  6 17:22:18 bryanc-desktop kernel: [    4.832021] usb 2-8: new high speed USB device using ehci_hcd and address 3
Feb  6 17:22:18 bryanc-desktop kernel: [    5.412038] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  6 17:22:18 bryanc-desktop kernel: [    5.420306] ata2.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Feb  6 17:22:18 bryanc-desktop kernel: [    5.420311] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb  6 17:22:18 bryanc-desktop kernel: [    5.436312] ata2.00: configured for UDMA/133
Feb  6 17:22:18 bryanc-desktop kernel: [    5.436430] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Feb  6 17:22:18 bryanc-desktop kernel: [    5.436551] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Feb  6 17:22:18 bryanc-desktop kernel: [    5.437106] scsi2 : sata_nv
Feb  6 17:22:18 bryanc-desktop kernel: [    5.437414] scsi3 : sata_nv
Feb  6 17:22:18 bryanc-desktop kernel: [    5.437667] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Feb  6 17:22:18 bryanc-desktop kernel: [    5.437671] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Feb  6 17:22:18 bryanc-desktop kernel: [    5.520097] usb 2-8: configuration #1 chosen from 1 choice
Feb  6 17:22:18 bryanc-desktop kernel: [    5.828020] usb 1-7: new low speed USB device using ohci_hcd and address 2
Feb  6 17:22:18 bryanc-desktop kernel: [    5.904038] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  6 17:22:18 bryanc-desktop kernel: [    5.912134] ata3.00: ATAPI: ATAPI   DVD A  DH16A6S, YA16, max UDMA/100
Feb  6 17:22:18 bryanc-desktop kernel: [    5.928138] ata3.00: configured for UDMA/100
Feb  6 17:22:18 bryanc-desktop kernel: [    6.043063] usb 1-7: configuration #1 chosen from 1 choice
Feb  6 17:22:18 bryanc-desktop kernel: [    6.052084] usbcore: registered new interface driver libusual
Feb  6 17:22:18 bryanc-desktop kernel: [    6.065084] Initializing USB Mass Storage driver...
Feb  6 17:22:18 bryanc-desktop kernel: [    6.077264] scsi4 : SCSI emulation for USB Mass Storage devices
Feb  6 17:22:18 bryanc-desktop kernel: [    6.078747] usbcore: registered new interface driver usb-storage
Feb  6 17:22:18 bryanc-desktop kernel: [    6.078753] USB Mass Storage support registered.
Feb  6 17:22:18 bryanc-desktop kernel: [    6.078882] usbcore: registered new interface driver hiddev
Feb  6 17:22:18 bryanc-desktop kernel: [    6.087290] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-7/1-7:1.0/input/input2
Feb  6 17:22:18 bryanc-desktop kernel: [    6.088902] scsi 1:0:0:0: Attached scsi generic sg0 type 0
Feb  6 17:22:18 bryanc-desktop kernel: [    6.092274] input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:02.0-7
Feb  6 17:22:18 bryanc-desktop kernel: [    6.092300] usbcore: registered new interface driver usbhid
Feb  6 17:22:18 bryanc-desktop kernel: [    6.092305] usbhid: v2.6:USB HID core driver
Feb  6 17:22:18 bryanc-desktop kernel: [    6.241072] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6S   YA16 PQ: 0 ANSI: 5
Feb  6 17:22:18 bryanc-desktop kernel: [    6.241281] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Feb  6 17:22:18 bryanc-desktop kernel: [    6.242100] scsi5 : pata_amd
Feb  6 17:22:18 bryanc-desktop kernel: [    6.242447] scsi6 : pata_amd
Feb  6 17:22:18 bryanc-desktop kernel: [    6.243541] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb  6 17:22:18 bryanc-desktop kernel: [    6.243545] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb  6 17:22:18 bryanc-desktop kernel: [    6.450019] Driver 'sd' needs updating - please use bus_type methods
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452255] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452275] sd 1:0:0:0: [sda] Write Protect is off
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452306] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452386] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452402] sd 1:0:0:0: [sda] Write Protect is off
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452431] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  6 17:22:18 bryanc-desktop kernel: [    6.452436]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Feb  6 17:22:18 bryanc-desktop kernel: [    6.474863]  sda1 sda2 < sda5 >
Feb  6 17:22:18 bryanc-desktop kernel: [    6.499754] sd 1:0:0:0: [sda] Attached SCSI disk
Feb  6 17:22:18 bryanc-desktop kernel: [    6.508201] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Feb  6 17:22:18 bryanc-desktop kernel: [    6.508208] Uniform CD-ROM driver Revision: 3.20
Feb  6 17:22:18 bryanc-desktop kernel: [    6.713068] PM: Starting manual resume from disk
Feb  6 17:22:18 bryanc-desktop kernel: [    6.737754] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  6 17:22:18 bryanc-desktop kernel: [    6.737759] EXT3-fs: write access will be enabled during recovery.
Feb  6 17:22:18 bryanc-desktop kernel: [    8.429109] kjournald starting.  Commit interval 5 seconds
Feb  6 17:22:18 bryanc-desktop kernel: [    8.429130] EXT3-fs: sda1: orphan cleanup on readonly fs
Feb  6 17:22:18 bryanc-desktop kernel: [    8.429183] EXT3-fs: sda1: 1 orphan inode deleted
Feb  6 17:22:18 bryanc-desktop kernel: [    8.429185] EXT3-fs: recovery complete.
Feb  6 17:22:18 bryanc-desktop kernel: [    8.437341] EXT3-fs: mounted filesystem with ordered data mode.
Feb  6 17:22:18 bryanc-desktop kernel: [   11.082507] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Feb  6 17:22:18 bryanc-desktop kernel: [   11.083696] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Feb  6 17:22:18 bryanc-desktop kernel: [   11.083857] sd 4:0:0:0: Attached scsi generic sg2 type 0
Feb  6 17:22:18 bryanc-desktop kernel: [   14.086707] udevd version 124 started
Feb  6 17:22:18 bryanc-desktop kernel: [   15.228258] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Feb  6 17:22:18 bryanc-desktop kernel: [   15.228298] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Feb  6 17:22:18 bryanc-desktop kernel: [   15.585847] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb  6 17:22:18 bryanc-desktop kernel: [   15.596051] ACPI: Power Button (FF) [PWRF]
Feb  6 17:22:18 bryanc-desktop kernel: [   15.596209] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Feb  6 17:22:18 bryanc-desktop kernel: [   15.612020] ACPI: Power Button (CM) [PWRB]
Feb  6 17:22:18 bryanc-desktop kernel: [   15.651158] ACPI: WMI: Mapper loaded
Feb  6 17:22:18 bryanc-desktop kernel: [   15.712179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  6 17:22:18 bryanc-desktop kernel: [   15.744230] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  6 17:22:18 bryanc-desktop kernel: [   16.616786] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Feb  6 17:22:18 bryanc-desktop kernel: [   16.616794] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Feb  6 17:22:18 bryanc-desktop kernel: [   19.126735] Linux agpgart interface v0.103
Feb  6 17:22:18 bryanc-desktop kernel: [   19.350361] nvidia: module license 'NVIDIA' taints kernel.
Feb  6 17:22:18 bryanc-desktop kernel: [   19.700954] input: PC Speaker as /devices/platform/pcspkr/input/input5
Feb  6 17:22:18 bryanc-desktop kernel: [   19.825680] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Feb  6 17:22:18 bryanc-desktop kernel: [   19.825688] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Feb  6 17:22:18 bryanc-desktop kernel: [   19.826069] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
Feb  6 17:22:18 bryanc-desktop kernel: [   20.446405] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Feb  6 17:22:18 bryanc-desktop kernel: [   22.059651] lp: driver loaded but no devices found
Feb  6 17:22:18 bryanc-desktop kernel: [   22.318653] Adding 2642652k swap on /dev/sda5.  Priority:-1 extents:1 across:2642652k
Feb  6 17:22:18 bryanc-desktop kernel: [   22.890101] EXT3 FS on sda1, internal journal
Feb  6 17:22:18 bryanc-desktop kernel: [   23.821311] type=1505 audit(1233958936.900:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4113
Feb  6 17:22:18 bryanc-desktop kernel: [   24.077271] type=1505 audit(1233958937.156:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4118
Feb  6 17:22:18 bryanc-desktop kernel: [   24.077565] type=1505 audit(1233958937.156:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4118
Feb  6 17:22:18 bryanc-desktop kernel: [   24.201054] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb  6 17:22:18 bryanc-desktop kernel: [   25.039457] powernow-k8: Found 1 AMD Athlon(tm) Processor 2650e processors (1 cpu cores) (version 2.20.00)
Feb  6 17:22:18 bryanc-desktop kernel: [   25.039496] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16
Feb  6 17:22:18 bryanc-desktop kernel: [   25.039500] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
Feb  6 17:22:18 bryanc-desktop kernel: [   25.770141] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb  6 17:22:18 bryanc-desktop kernel: [   25.845294] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb  6 17:22:18 bryanc-desktop kernel: [   25.845302] apm: overridden by ACPI.
Feb  6 17:22:19 bryanc-desktop kernel: [   26.018290] ppdev: user-space parallel port driver
Feb  6 17:22:20 bryanc-desktop kernel: [   27.736155] Bluetooth: Core ver 2.13
Feb  6 17:22:20 bryanc-desktop kernel: [   27.737874] NET: Registered protocol family 31
Feb  6 17:22:20 bryanc-desktop kernel: [   27.737880] Bluetooth: HCI device and connection manager initialized
Feb  6 17:22:20 bryanc-desktop kernel: [   27.737885] Bluetooth: HCI socket layer initialized
Feb  6 17:22:20 bryanc-desktop kernel: [   27.778415] Bluetooth: L2CAP ver 2.11
Feb  6 17:22:20 bryanc-desktop kernel: [   27.778421] Bluetooth: L2CAP socket layer initialized
Feb  6 17:22:20 bryanc-desktop kernel: [   27.807402] Bluetooth: RFCOMM socket layer initialized
Feb  6 17:22:20 bryanc-desktop kernel: [   27.810268] Bluetooth: RFCOMM TTY layer initialized
Feb  6 17:22:20 bryanc-desktop kernel: [   27.810274] Bluetooth: RFCOMM ver 1.10
Feb  6 17:22:20 bryanc-desktop kernel: [   27.811063] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  6 17:22:20 bryanc-desktop kernel: [   27.811069] Bluetooth: BNEP filters: protocol multicast
Feb  6 17:22:20 bryanc-desktop kernel: [   27.855655] Bridge firewalling registered
Feb  6 17:22:20 bryanc-desktop kernel: [   27.878245] Bluetooth: SCO (Voice Link) ver 0.6
Feb  6 17:22:20 bryanc-desktop kernel: [   27.878252] Bluetooth: SCO socket layer initialized
Feb  6 17:22:22 bryanc-desktop kernel: [   29.500026] Clocksource tsc unstable (delta = -249899136 ns)
Feb  6 17:22:25 bryanc-desktop kernel: [   32.132142] NET: Registered protocol family 17
Feb  6 17:22:30 bryanc-desktop kernel: [   37.376179] NET: Registered protocol family 10
Feb  6 17:22:30 bryanc-desktop kernel: [   37.380242] lo: Disabled Privacy Extensions
Feb  6 17:22:39 bryanc-desktop pulseaudio[5508]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  6 17:22:39 bryanc-desktop pulseaudio[5510]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  6 17:22:39 bryanc-desktop pulseaudio[5510]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  6 17:42:17 bryanc-desktop -- MARK --
```

---

### Post by mjheagle8 on 2009-02-07
can you post a log of a time that the computer crashed?

---

### Post by Raskula on 2009-02-07
I posted the log of the whole day. Feb 6 is when it crashed...

---

### Post by Monotoko on 2009-02-07
Yeah but what time on that day?

---

### Post by Raskula on 2009-02-07
I don't remember. I posted everything for that day though.

---

### Post by mjheagle8 on 2009-02-07
we need to know when approximately because otherwise we cant tell where the errors are.

---

### Post by Raskula on 2009-02-07
Can't you just look threw it like the people at Fedora did? I'm guessing its near the end because it happened before I went to bed I think. The fedora people just fixed all the errors that they saw, but it still didn't solve the problem. So I switched to Ubuntu and it was happening with it too.

---

### Post by Monotoko on 2009-02-07
so what good would fixing it all again do? Most computers running ubuntu have 1 or 2 problems, but they dont affect the average user.

We need to fix this problem your having, which the guys at fedora couldnt do, as you said. So we need to highlight an exact (or approx) point at which the error occured.

---

### Post by Kevbert on 2009-02-07
In your home folder there's a hidden log file that may help. Please open Nautilus in your home folder, press Ctrl-H (to show hidden files) and post the .xsession-errors file (the '.' means it's normally hidden).

---

### Post by Raskula on 2009-02-07
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
x-session-manager[5393]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:5615): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

x-session-manager[5393]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
starting HAL detection for ac adaptors...
** (nm-applet:5660): WARNING **: No connections defined
none found
evolution-alarm-notify-Message: Setting timeout for 16726 1234051200 1234034474
evolution-alarm-notify-Message:  Sat Feb  7 19:00:00 2009

evolution-alarm-notify-Message:  Sat Feb  7 14:21:14 2009

Throttle level is 0
ICEDTEAPLUGIN_DEBUG = (null)
/opt/lampp/lampp: line 195: echo: write error: Broken pipe
/opt/lampp/lampp: line 228: echo: write error: Broken pipe
/opt/lampp/bin/mysql.server: 84: source: not found
/opt/lampp/lampp: line 301: echo: write error: Broken pipe
/opt/lampp/lampp: line 118: echo: write error: Broken pipe
/opt/lampp/bin/mysql.server: 334: log_success_msg: not found
/opt/lampp/lampp: line 336: echo: write error: Broken pipe
/opt/lampp/lampp: line 384: echo: write error: Broken pipe
/opt/lampp/lampp: line 412: echo: write error: Broken pipe
/opt/lampp/lampp: line 327: echo: write error: Broken pipe
AL lib: alcConfig.c:228: Reading ~/.openalrc; this file is deprecated
	Please rename it to ~/.alsoftrc
AL lib: alcConfig.c:141: config parse error: option without a value: "(define"
Found 2 messages leaked
ICEDTEAPLUGIN_DEBUG = (null)
```

Also when it crashed, I had to hold the power button down because that was the only way to get out of the crash.

---

### Post by thesubmitter on 2009-03-22
Incidentally, I'm having this same issue with Debian Lenny 2.2.26 AMD64 Kernel

I installed it for my parents (going for the conversion no less) and this ridiculous crash would happen COMPLETELY randomly as far as I could tell except that X was running.

It would crash and make the distorted "dashes" as explained in the fedora post and then it crashes my router if plugged in via ethernet (hyperwrt WRT54G) so that none of the LAN ports work but the WiFi would still work.

I couldn't get anything from the logs perhaps because the log files are locked when the crash happens or something , I couldn't switch terminals and because of the router crash - I couldn't even try to SSH in....

Very frustrating especially that I was trying to get my parents to switch to Linux and this happened....

Thanks!

---

