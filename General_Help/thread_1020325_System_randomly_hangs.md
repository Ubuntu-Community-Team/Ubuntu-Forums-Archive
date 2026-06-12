---
title: "System randomly hangs"
date: 2008-12-24
forum: General Help
---

### Post by todlangweilig on 2008-12-24
It seems that my computer has solidly locked up 3 times in the last 4 days. I can't seem to find any rhyme or reason to it as well, and it has also occurred in previous versions of Ubuntu. The screen will simply freeze, and keyboard and mouse input does nothing. I think it has frozen when I've been using the mouse, when the computer has been idle for a few minutes, or when it has been idle for a long time and the screen has blanked. I don't know if these are related or different causes with the same symptoms. 

I can't switch to another terminal, restart X, or do Alt-Sys Req REISUB. Nothing is left in any of the logs about this as well, a brief excerpt of /var/log/messages is below. It is noteworthy that my computer's fan goes to the highest setting as well, which it never does during normal processing, even at full utilization for hours. (This may be due to changing the cooling mood from 'quiet' to 'performance' recently, I haven't stress tested the cpu in a while to find out if the fan will turn on high.)

This is really frustrating me, I don't like losing whatever work I had open on a frequent basis. It also seems to be occur more with the later versions of Ubuntu than the previous. I'm out of ideas to try, and I can't figure out how to reproduce it.  

[HTML]
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.319604] Registered led device: iwl-phy0:TX
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.418971] [drm] Initialized drm 1.1.0 20060810
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.424920] pci 0000:00:02.0: power state changed by ACPI to D0
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.424938] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.425145] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.445973] NET: Registered protocol family 17
Dec 24 00:03:48 aaron-m405-laptop kernel: [   31.794707] 0000:01:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 24 00:03:48 aaron-m405-laptop kernel: [   31.794715] 0000:01:00.0: eth0: 10/100 speed: disabling TSO
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5754]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5756]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5756]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.717985] NET: Registered protocol family 10
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.719052] lo: Disabled Privacy Extensions
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.722724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 24 00:10:18 aaron-m405-laptop kernel: [  421.232080] CE: hpet increasing min_delta_ns to 15000 nsec
Dec 24 00:23:39 aaron-m405-laptop -- MARK --
Dec 24 00:30:44 aaron-m405-laptop syslogd 1.5.0#2ubuntu6: restart.
Dec 24 00:43:39 aaron-m405-laptop -- MARK --
Dec 24 01:03:39 aaron-m405-laptop -- MARK --[/HTML]

---

### Post by nerktord on 2008-12-24
I have a very similar problem, see my thread "ubuntu 8.10 keeps freezing"..all the symptoms you describe is kinda equal to mine, only mine happens more often. I never had this either in previous versions such as 8.04, I'm wondering what it could be.

---

### Post by todlangweilig on 2008-12-24
Thank you for your reply. Indeed, it does seem to be every similar. I don't know if Firefox has something to do with this or not, I have it open so much, I can't remember if it has crashed when FF wasn't open. I haven't had to use the noacpi, nolacpi flags to boot, I don't know if that is significant here or not.  

For other, heres the link: [http://ubuntuforums.org/showthread.php?t=1020157](http://ubuntuforums.org/showthread.php?t=1020157)

I think I may have posted the wrong section of time from /var/log/messages, so here is the whole thing for today.

[HTML]Dec 24 00:03:39 aaron-m405-laptop syslogd 1.5.0#2ubuntu6: restart.
Dec 24 00:03:39 aaron-m405-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 24 00:03:40 aaron-m405-laptop kernel: Cannot find map file.
Dec 24 00:03:40 aaron-m405-laptop kernel: Loaded 52994 symbols from 103 modules.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f750000 (usable)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 000000003f750000 - 0000000040000000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec18000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec20000 - 00000000fec28000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] last_pfn = 0x3f750 max_arch_pfn = 0x100000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] RAMDISK: 3781d000 - 37fefda2
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] DMI 2.4 present.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: RSDP 000F01E0, 0014 (r0 TOSHIB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: RSDT 3F750000, 0050 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: FACP 3F750080, 0084 (r2 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: DSDT 3F750104, 4C74 (r2 TOSHIB A003C    20071207 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: SSDT 3F754D78, 0306 (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: DBGP 3F7559D4, 0034 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: BOOT 3F750058, 0028 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: APIC 3F755930, 0068 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: MCFG 3F755998, 003C (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: HPET 3F755A08, 0038 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: SLIC 3F755A40, 0176 (r1 TOSHIB A003C    20060821 TASM  4010000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: SSDT 3F755BE8, 092C (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: SSDT 3F75805A, 1574 (r2 TOSHIB A003C    20070222 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: SSDT 3F7595CE, 0081 (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: DMI detected: Toshiba
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] 119MB HIGHMEM available.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] 896MB LOWMEM available.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   low ram: 00000000 - 38000000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #4 [003781d000 - 0037fefda2]          RAMDISK ==> [003781d000 - 0037fefda2]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #6 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Zone PFN ranges:
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0003f750
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Movable zone start PFN for each node
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009e
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003f750
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257537
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Kernel command line: root=UUID=ef83b91f-49ea-4269-85f5-4cf76b6000b7 ro quiet splash 
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Initializing CPU#0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] TSC: using PIT calibration value
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.000000] Detected 1828.724 MHz processor.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] console [tty0] enabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Memory: 1015916k/1039680k available (2572k kernel code, 22964k reserved, 1160k data, 424k init, 122176k highmem)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] virtual kernel memory layout:
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.44 BogoMIPS (lpj=7314896)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Security Framework initialized
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Initializing cgroup subsys ns
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Initializing cgroup subsys memory
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] using mwait in idle threads.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.018414] ACPI: Core revision 20080609
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.020335] ACPI: Checking initramfs for custom DSDT
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.400163] ENABLING IO-APIC IRQs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.400360] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.440061] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.444027] Booting processor 1/1 ip 6000
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Initializing CPU#1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3657.57 BogoMIPS (lpj=7315152)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.528551] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.528575] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532055] Brought up 2 CPUs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532059] Total of 2 processors activated (7315.02 BogoMIPS).
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532196] net_namespace: 840 bytes
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532196] Booting paravirtualized kernel on bare hardware
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532326] Time:  0:03:17  Date: 12/24/08
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532359] NET: Registered protocol family 16
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] EISA bus registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] ACPI: bus type pci registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] PCI: Not using MMCONFIG.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] PCI: PCI BIOS revision 2.10 entry at 0xfd123, last bus=4
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.532383] PCI: Using configuration type 1 for base access
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.540222] ACPI Warning (dsobject-0501): Package List length (C) larger than NumElements count (3), truncated
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.540228]  [20080609]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.542987] ACPI: Interpreter enabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.542991] ACPI: (supports S0 S3 S4 S5)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.543008] ACPI: Using IOAPIC for interrupt routing
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.543070] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.548183] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.548187] PCI: Using MMCONFIG for extended config space
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1b.0: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1c.0: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556753] pci 0000:00:1c.2: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556838] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.556844] pci 0000:00:1d.7: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557002] pci 0000:00:1f.0: quirk: region d800-d87f claimed by ICH6 ACPI/GPIO/TCO
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557007] pci 0000:00:1f.0: quirk: region eec0-eeff claimed by ICH6 GPIO
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557303] pci 0000:00:1f.2: PME# supported from D3hot
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557308] pci 0000:00:1f.2: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557511] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.557519] pci 0000:01:00.0: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560285] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560299] pci 0000:02:00.0: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560455] pci 0000:03:0b.0: PME# supported from D0 D1 D2 D3hot
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560461] pci 0000:03:0b.0: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560575] pci 0000:03:0b.1: PME# supported from D0 D1 D2 D3hot
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560581] pci 0000:03:0b.1: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560691] pci 0000:03:0b.2: PME# supported from D0 D1 D2 D3hot
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560697] pci 0000:03:0b.2: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560803] pci 0000:03:0b.3: PME# supported from D0 D1 D2 D3hot
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560809] pci 0000:03:0b.3: PME# disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.560855] pci 0000:00:1e.0: transparent bridge
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.564548] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.564548] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.564599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.564812] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.565026] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.565323] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.565537] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.568094] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.568384] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.568399] pnp: PnP ACPI init
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.568399] ACPI: bus type pnp registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.576986] pnp: PnP ACPI: found 13 devices
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.576989] ACPI: ACPI bus type pnp unregistered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.576992] PnPBIOS: Disabled by ACPI PNP
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.577013] PCI: Using ACPI for IRQ routing
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584041] NET: Registered protocol family 8
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584044] NET: Registered protocol family 20
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584066] NetLabel: Initializing
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584066] NetLabel:  domain hash size = 128
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584066] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584075] NetLabel:  unlabeled traffic allowed by default
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584084] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.584089] hpet0: 3 64-bit timers, 14318180 Hz
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.585684] tracer: 772 pages allocated for 65536 entries of 48 bytes
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.585687]    actual entries 65620
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.585780] AppArmor: AppArmor Filesystem Enabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.585808] ACPI: RTC can wake from S4
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592025] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592028] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592032] system 00:00: iomem range 0x100000-0x3f74ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592036] system 00:00: iomem range 0x3f750000-0x3f75ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592040] system 00:00: iomem range 0x3f760000-0x3f7fffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592043] system 00:00: iomem range 0x3f800000-0x3fffffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592047] system 00:00: iomem range 0xfec00000-0xfec17fff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592051] system 00:00: iomem range 0xfec20000-0xfec27fff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592054] system 00:00: iomem range 0xfed14000-0xfed19fff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592058] system 00:00: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592062] system 00:00: iomem range 0xfed20000-0xfed3ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592065] system 00:00: iomem range 0xfed45000-0xfed8ffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592069] system 00:00: iomem range 0xfeda0000-0xfedbffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592073] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592076] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592080] system 00:00: iomem range 0xffe00000-0xffffffff could not be reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592087] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592100] system 00:09: ioport range 0x1e0-0x1ef has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592103] system 00:09: ioport range 0x480-0x48f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592107] system 00:09: ioport range 0xe000-0xe07f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592110] system 00:09: ioport range 0xe080-0xe0ff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592114] system 00:09: ioport range 0xe400-0xe47f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592117] system 00:09: ioport range 0xe480-0xe4ff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592120] system 00:09: ioport range 0xe800-0xe87f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592124] system 00:09: ioport range 0xe880-0xe8ff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592127] system 00:09: ioport range 0xec00-0xec7f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592131] system 00:09: ioport range 0xec80-0xecff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592134] system 00:09: ioport range 0xd800-0xd87f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592138] system 00:09: ioport range 0xd880-0xd89f has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592141] system 00:09: ioport range 0xeeb0-0xeebf has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592145] system 00:09: ioport range 0xeec0-0xeeff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592148] system 00:09: ioport range 0x690-0x6ff has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.592155] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627422] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627427] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627434] pci 0000:00:1c.0:   MEM window: 0xffc00000-0xffcfffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627440] pci 0000:00:1c.0:   PREFETCH window: disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627448] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627451] pci 0000:00:1c.2:   IO window: disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627458] pci 0000:00:1c.2:   MEM window: 0xffa00000-0xffafffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627463] pci 0000:00:1c.2:   PREFETCH window: disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627494] pci 0000:03:0b.0: CardBus bridge, secondary bus 0000:04
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627497] pci 0000:03:0b.0:   IO window: 0x001000-0x0010ff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627503] pci 0000:03:0b.0:   IO window: 0x001400-0x0014ff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627510] pci 0000:03:0b.0:   PREFETCH window: 0x50000000-0x53ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627516] pci 0000:03:0b.0:   MEM window: 0x54000000-0x57ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627522] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627526] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627533] pci 0000:00:1e.0:   MEM window: 0x54000000-0x59ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627539] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627559] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627576] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627601] pci 0000:03:0b.0: enabling device (0000 -> 0003)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627606] pci 0000:03:0b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627615] bus: 00 index 0 io port: [0, ffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627618] bus: 00 index 1 mmio: [0, ffffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627621] bus: 01 index 0 io port: [b000, bfff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627623] bus: 01 index 1 mmio: [ffc00000, ffcfffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627626] bus: 01 index 2 mmio: [0, 0]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627628] bus: 01 index 3 mmio: [0, 0]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627630] bus: 02 index 0 mmio: [0, 0]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627633] bus: 02 index 1 mmio: [ffa00000, ffafffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627635] bus: 02 index 2 mmio: [0, 0]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627638] bus: 02 index 3 mmio: [0, 0]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627640] bus: 03 index 0 io port: [1000, 1fff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627643] bus: 03 index 1 mmio: [54000000, 59ffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627646] bus: 03 index 2 mmio: [50000000, 53ffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627648] bus: 03 index 3 io port: [0, ffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627651] bus: 03 index 4 mmio: [0, ffffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627653] bus: 04 index 0 io port: [1000, 10ff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627656] bus: 04 index 1 io port: [1400, 14ff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627658] bus: 04 index 2 mmio: [50000000, 53ffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627661] bus: 04 index 3 mmio: [54000000, 57ffffff]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.627671] NET: Registered protocol family 2
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.640057] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.640315] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.640828] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.641108] TCP: Hash tables configured (established 131072 bind 65536)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.641112] TCP reno registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.648098] NET: Registered protocol family 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    0.648235] checking if image is initramfs... it is
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.415995] Freeing initrd memory: 8011k freed
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.416417] Simple Boot Flag value 0xb read from CMOS RAM was invalid
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.416421] Simple Boot Flag at 0x7c set to 0x1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.417409] audit: initializing netlink socket (disabled)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.417438] type=2000 audit(1230076997.416:1): initialized
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.424237] highmem bounce pool size: 64 pages
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.424244] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427221] VFS: Disk quotas dquot_6.5.1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427328] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427454] msgmni has been set to 1762
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427594] io scheduler noop registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427598] io scheduler anticipatory registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427600] io scheduler deadline registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427614] io scheduler cfq registered (default)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.427913] pcieport-driver 0000:00:1c.0: found MSI capability
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.428192] pcieport-driver 0000:00:1c.2: found MSI capability
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.428672] isapnp: Scanning for PnP cards...
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.782374] isapnp: No Plug & Play device found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.823851] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.824830] 00:0c: ttyS0 at I/O 0x338 (irq = 4) is a 16550A
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.826845] brd: module loaded
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.826929] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.827071] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.831940] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.831948] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832446] mice: PS/2 mouse device common for all mice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832598] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832631] rtc0: alarms up to one year, hpet irqs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832779] EISA: Probing bus 0 at eisa.0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832786] Cannot allocate resource for EISA slot 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832817] EISA: Detected 0 cards.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832821] cpuidle: using governor ladder
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.832824] cpuidle: using governor menu
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833402] TCP cubic registered
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833434] Using IPI No-Shortcut mode
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833651] registered taskstats version 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833801]   Magic number: 4:350:52
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833909] rtc_cmos 00:08: setting system clock to 2008-12-24 00:03:18 UTC (1230076998)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833913] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.833916] EDD information not available.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.834178] Freeing unused kernel memory: 424k freed
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.834230] Write protecting the kernel text: 2576k
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.834262] Write protecting the kernel read-only data: 936k
Dec 24 00:03:40 aaron-m405-laptop kernel: [    1.851668] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.033159] fuse init (API version 7.9)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.081267] ACPI: SSDT 3F7553C0, 00F3 (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.081622] ACPI: SSDT 3F755529, 034E (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.082255] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.082318] processor ACPI0007:00: registered as cooling_device0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.082437] ACPI: SSDT 3F7554B3, 0076 (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.082750] ACPI: SSDT 3F755877, 0079 (r2 TOSHIB A003C    20060907 MSFT  100000E)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.083399] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.083456] processor ACPI0007:01: registered as cooling_device1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.086198] thermal LNXTHERM:01: registered as thermal_zone0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.086359] ACPI: Thermal Zone [THRM] (43 C)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.097020] Marking TSC unstable due to TSC halts in idle
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.385082] ACPI: ACPI Dock Station Driver
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.519978] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.519982] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.520045] e1000e 0000:01:00.0: Disabling L1 ASPM
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.520073] e1000e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.557486] usbcore: registered new interface driver usbfs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.557514] usbcore: registered new interface driver hub
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.557562] usbcore: registered new device driver usb
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.559944] USB Universal Host Controller Interface driver v3.0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.579455] 0000:01:00.0: 0000:01:00.0: Warning: detected ASPM enabled in EEPROM
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.626761] SCSI subsystem initialized
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640300] 0000:01:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:0e:7b:80:3d:e5
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640304] 0000:01:00.0: eth0: Intel(R) PRO/1000 Network Connection
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640382] 0000:01:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640460] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640476] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640522] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640562] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000afe0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640747] usb usb1: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640780] hub 1-0:1.0: USB hub found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.640788] hub 1-0:1.0: 2 ports detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744371] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744388] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744420] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744460] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000af80
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744572] usb usb2: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744604] hub 2-0:1.0: USB hub found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.744612] hub 2-0:1.0: 2 ports detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952372] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952419] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952462] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000af60
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952582] usb usb3: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952613] hub 3-0:1.0: USB hub found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    2.952622] hub 3-0:1.0: 2 ports detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056518] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056534] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056562] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056601] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000af40
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056705] usb usb4: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056736] hub 4-0:1.0: USB hub found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.056743] hub 4-0:1.0: 2 ports detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.064121] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.160589] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.160610] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.160636] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.164541] ehci_hcd 0000:00:1d.7: debug port 1
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.164558] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffd3fc00
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.188479] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.188683] usb usb5: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.188716] hub 5-0:1.0: USB hub found
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.188726] hub 5-0:1.0: 8 ports detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.396602] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.396655] pata_acpi 0000:00:1f.1: PCI INT A disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.396688] ohci1394 0000:03:0b.1: enabling device (0000 -> 0002)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.396698] ohci1394 0000:03:0b.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.409050] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.409148] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.409153] ahci 0000:00:1f.2: flags: 64bit ncq ilck pm led clo pio slum part 
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.421058] scsi0 : ahci
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.421173] scsi1 : ahci
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.421252] scsi2 : ahci
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.421328] scsi3 : ahci
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.422663] ata1: SATA max UDMA/133 abar m1024@0xffd3f800 port 0xffd3f900 irq 221
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.422667] ata2: DUMMY
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.422670] ata3: SATA max UDMA/133 abar m1024@0xffd3f800 port 0xffd3fa00 irq 221
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.422673] ata4: DUMMY
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.446437] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[58006000-580067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.500120] Clocksource tsc unstable (delta = -300144563 ns)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.740147] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.741510] ata1.00: ATA-7: HTS541010G9SA00, MBZOC60D, max UDMA/100
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.741513] ata1.00: 195371568 sectors, multi 0: LBA48 NCQ (not used)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    3.743102] ata1.00: configured for UDMA/100
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.076143] ata3: SATA link down (SStatus 0 SControl 300)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.092332] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9SA00  MBZO PQ: 0 ANSI: 5
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.101979] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.102114] scsi4 : ata_piix
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.102214] scsi5 : ata_piix
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.103125] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xaf10 irq 14
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.103129] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xaf18 irq 15
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.113382] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.116046] usb 2-1: new full speed USB device using uhci_hcd and address 4
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.125772] Driver 'sd' needs updating - please use bus_type methods
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126573] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126604] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126648] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126744] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126767] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126811] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.126816]  sda:<6>ata5.00: ATAPI: MATSHITADVD-RAM UJ-842S, 1.01, max UDMA/33
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.280598] ata5.00: configured for UDMA/33
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.282688] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-842S  1.01 PQ: 0 ANSI: 5
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.282877] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.288645] usb 2-1: configuration #1 chosen from 1 choice
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.302811] Driver 'sr' needs updating - please use bus_type methods
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.502177]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.556082] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.563804] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 24 00:03:40 aaron-m405-laptop kernel: [    4.563809] Uniform CD-ROM driver Revision: 3.20
Dec 24 00:03:40 aaron-m405-laptop kernel: [    5.070211] PM: Starting manual resume from disk
Dec 24 00:03:40 aaron-m405-laptop kernel: [    5.089455] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    5.089459] EXT3-fs: write access will be enabled during recovery.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    8.088256] kjournald starting.  Commit interval 5 seconds
Dec 24 00:03:40 aaron-m405-laptop kernel: [    8.088279] EXT3-fs: sda7: orphan cleanup on readonly fs
Dec 24 00:03:40 aaron-m405-laptop kernel: [    8.088325] EXT3-fs: sda7: 1 orphan inode deleted
Dec 24 00:03:40 aaron-m405-laptop kernel: [    8.088328] EXT3-fs: recovery complete.
Dec 24 00:03:40 aaron-m405-laptop kernel: [    8.111852] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   15.351023] udevd version 124 started
Dec 24 00:03:40 aaron-m405-laptop kernel: [   15.916910] iTCO_vendor_support: vendor-support=0
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.074770] Linux agpgart interface v0.103
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.174651] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.175199] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.191996] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.266908] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.348132] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.397682] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.399825] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0xd860)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.399956] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.730685] ACPI: AC Adapter [ADP1] (on-line)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.822195] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.840158] ACPI: Power Button (FF) [PWRF]
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.840308] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.840390] ACPI: Lid Switch [LID]
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.840478] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.872037] ACPI: Power Button (CM) [PWRB]
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.873224] ACPI: Battery Slot [BAT1] (battery present)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   16.873286] ACPI: Battery Slot [BAT2] (battery absent)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.095393] Yenta: CardBus bridge found at 0000:03:0b.0 [1179:0001]
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.095417] Yenta: Enabling burst memory read transactions
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.095423] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.095426] Yenta: Routing CardBus interrupts to PCI
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.095432] Yenta TI: socket 0000:03:0b.0, mfunc 0x01aa1022, devctl 0x64
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.117985] sdhci: Secure Digital Host Controller Interface driver
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.117990] sdhci: Copyright(c) Pierre Ossman
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.184198] acpi device:0d: registered as cooling_device2
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.184443] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/input/input5
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.204788] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.204849] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.216032] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.324830] Yenta: ISA IRQ mask 0x0cf8, PCI irq 21
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.324836] Socket status: 30000006
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.324840] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.324847] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.324850] cs: IO port probe 0x1000-0x1fff: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.325085] pcmcia: parent PCI bridge Memory window: 0x54000000 - 0x59ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.325088] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331449] tifm_7xx1 0000:03:0b.2: enabling device (0000 -> 0002)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331458] tifm_7xx1 0000:03:0b.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331559] sdhci-pci 0000:03:0b.3: SDHCI controller found [104c:803c] (rev 0)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331575] sdhci-pci 0000:03:0b.3: enabling device (0000 -> 0002)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331580] sdhci-pci 0000:03:0b.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.331648] mmc0: SDHCI controller on PCI [0000:03:0b.3] using DMA
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.335077] intel_rng: FWH not detected
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.346243] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.346297] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.437436] input: PC Speaker as /devices/platform/pcspkr/input/input6
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.439220] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.439275] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x680, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.748072] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.748077] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.748704] iwl3945 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.748744] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Dec 24 00:03:40 aaron-m405-laptop kernel: [   17.843156] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.131279] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.186056] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.331173] iwl3945 0000:02:00.0: PCI INT A disabled
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.572602] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.572612] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.572624] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.792603] cs: IO port probe 0x100-0x3af: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.794486] cs: IO port probe 0x3e0-0x4ff: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.795266] cs: IO port probe 0x820-0x8ff: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.795952] cs: IO port probe 0xc00-0xcf7: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   18.796862] cs: IO port probe 0xa00-0xaff: clean.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   19.381602] lp: driver loaded but no devices found
Dec 24 00:03:40 aaron-m405-laptop kernel: [   19.578212] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k
Dec 24 00:03:40 aaron-m405-laptop kernel: [   20.125871] EXT3 FS on sda7, internal journal
Dec 24 00:03:40 aaron-m405-laptop kernel: [   20.903642] kjournald starting.  Commit interval 5 seconds
Dec 24 00:03:40 aaron-m405-laptop kernel: [   20.904070] EXT3 FS on sda6, internal journal
Dec 24 00:03:40 aaron-m405-laptop kernel: [   20.904080] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   21.067421] type=1505 audit(1230095017.846:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4283
Dec 24 00:03:40 aaron-m405-laptop kernel: [   21.270484] type=1505 audit(1230095018.050:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4288
Dec 24 00:03:40 aaron-m405-laptop kernel: [   21.270702] type=1505 audit(1230095018.050:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4288
Dec 24 00:03:40 aaron-m405-laptop kernel: [   21.451998] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 24 00:03:40 aaron-m405-laptop kernel: [   22.460223] toshiba_acpi: Toshiba Laptop ACPI Extras version experimental-dev-toshiba-test-5
Dec 24 00:03:40 aaron-m405-laptop kernel: [   22.460228] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
Dec 24 00:03:40 aaron-m405-laptop kernel: [   22.480189] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   22.480879] ACPI: Error installing bay notify handler
Dec 24 00:03:40 aaron-m405-laptop kernel: [   22.579640] ACPI: WMI: Mapper loaded
Dec 24 00:03:40 aaron-m405-laptop kernel: [   23.486453] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Dec 24 00:03:40 aaron-m405-laptop kernel: [   23.557956] apm: BIOS not found.
Dec 24 00:03:40 aaron-m405-laptop kernel: [   23.706096] ppdev: user-space parallel port driver
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.733381] Bluetooth: Core ver 2.13
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.733584] NET: Registered protocol family 31
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.733592] Bluetooth: HCI device and connection manager initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.733602] Bluetooth: HCI socket layer initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.760143] Bluetooth: L2CAP ver 2.11
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.760154] Bluetooth: L2CAP socket layer initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.779313] Bluetooth: SCO (Voice Link) ver 0.6
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.779324] Bluetooth: SCO socket layer initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.794561] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.794576] Bluetooth: BNEP filters: protocol multicast
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.859174] Bridge firewalling registered
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.883481] Bluetooth: RFCOMM socket layer initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.883508] Bluetooth: RFCOMM TTY layer initialized
Dec 24 00:03:42 aaron-m405-laptop kernel: [   25.883512] Bluetooth: RFCOMM ver 1.10
Dec 24 00:03:46 aaron-m405-laptop kernel: [   30.181583] iwl3945 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 24 00:03:46 aaron-m405-laptop kernel: [   30.186028] firmware: requesting iwlwifi-3945-1.ucode
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.319444] Registered led device: iwl-phy0:radio
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.319535] Registered led device: iwl-phy0:assoc
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.319571] Registered led device: iwl-phy0:RX
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.319604] Registered led device: iwl-phy0:TX
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.418971] [drm] Initialized drm 1.1.0 20060810
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.424920] pci 0000:00:02.0: power state changed by ACPI to D0
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.424938] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.425145] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 24 00:03:47 aaron-m405-laptop kernel: [   30.445973] NET: Registered protocol family 17
Dec 24 00:03:48 aaron-m405-laptop kernel: [   31.794707] 0000:01:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 24 00:03:48 aaron-m405-laptop kernel: [   31.794715] 0000:01:00.0: eth0: 10/100 speed: disabling TSO
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5754]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5756]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 24 00:04:15 aaron-m405-laptop pulseaudio[5756]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.717985] NET: Registered protocol family 10
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.719052] lo: Disabled Privacy Extensions
Dec 24 00:05:51 aaron-m405-laptop kernel: [  154.722724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 24 00:10:18 aaron-m405-laptop kernel: [  421.232080] CE: hpet increasing min_delta_ns to 15000 nsec
Dec 24 00:23:39 aaron-m405-laptop -- MARK --
Dec 24 00:30:44 aaron-m405-laptop syslogd 1.5.0#2ubuntu6: restart.
Dec 24 00:43:39 aaron-m405-laptop -- MARK --
Dec 24 01:03:39 aaron-m405-laptop -- MARK --
Dec 24 01:23:39 aaron-m405-laptop -- MARK --
Dec 24 01:43:39 aaron-m405-laptop -- MARK --[/HTML]

Here is also the output from dmesg:
[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f750000 (usable)
[    0.000000]  BIOS-e820: 000000003f750000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec18000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec20000 - 00000000fec28000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3f750 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fefda2
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F01E0, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 3F750000, 0050 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: FACP 3F750080, 0084 (r2 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: DSDT 3F750104, 4C74 (r2 TOSHIB A003C    20071207 MSFT  100000E)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: SSDT 3F754D78, 0306 (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    0.000000] ACPI: DBGP 3F7559D4, 0034 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: BOOT 3F750058, 0028 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: APIC 3F755930, 0068 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: MCFG 3F755998, 003C (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: HPET 3F755A08, 0038 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: SLIC 3F755A40, 0176 (r1 TOSHIB A003C    20060821 TASM  4010000)
[    0.000000] ACPI: SSDT 3F755BE8, 092C (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F75805A, 1574 (r2 TOSHIB A003C    20070222 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7595CE, 0081 (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781d000 - 0037fefda2]          RAMDISK ==> [003781d000 - 0037fefda2]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003f750
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0003f750
[    0.000000] On node 0 totalpages: 259822
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 30275 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257537
[    0.000000] Kernel command line: root=UUID=ef83b91f-49ea-4269-85f5-4cf76b6000b7 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1828.724 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1015916k/1039680k available (2572k kernel code, 22964k reserved, 1160k data, 424k init, 122176k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.44 BogoMIPS (lpj=7314896)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018414] ACPI: Core revision 20080609
[    0.020335] ACPI: Checking initramfs for custom DSDT
[    0.400163] ENABLING IO-APIC IRQs
[    0.400360] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.440061] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[    0.444027] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3657.57 BogoMIPS (lpj=7315152)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.528551] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[    0.528575] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.532055] Brought up 2 CPUs
[    0.532059] Total of 2 processors activated (7315.02 BogoMIPS).
[    0.532083] CPU0 attaching sched-domain:
[    0.532087]  domain 0: span 0-1 level MC
[    0.532090]   groups: 0 1
[    0.532097] CPU1 attaching sched-domain:
[    0.532100]  domain 0: span 0-1 level MC
[    0.532102]   groups: 1 0
[    0.532196] net_namespace: 840 bytes
[    0.532196] Booting paravirtualized kernel on bare hardware
[    0.532326] Time:  0:03:17  Date: 12/24/08
[    0.532359] NET: Registered protocol family 16
[    0.532383] EISA bus registered
[    0.532383] ACPI: bus type pci registered
[    0.532383] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.532383] PCI: Not using MMCONFIG.
[    0.532383] PCI: PCI BIOS revision 2.10 entry at 0xfd123, last bus=4
[    0.532383] PCI: Using configuration type 1 for base access
[    0.536326] ACPI: EC: Look up EC in DSDT
[    0.540222] ACPI Warning (dsobject-0501): Package List length (C) larger than NumElements count (3), truncated
[    0.540228]  [20080609]
[    0.542987] ACPI: Interpreter enabled
[    0.542991] ACPI: (supports S0 S3 S4 S5)
[    0.543008] ACPI: Using IOAPIC for interrupt routing
[    0.543070] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.548183] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.548187] PCI: Using MMCONFIG for extended config space
[    0.556753] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.556753] PCI: 0000:00:02.0 reg 10 32bit mmio: [ffd80000, ffdfffff]
[    0.556753] PCI: 0000:00:02.0 reg 14 io port: [cff8, cfff]
[    0.556753] PCI: 0000:00:02.0 reg 18 32bit mmio: [e0000000, efffffff]
[    0.556753] PCI: 0000:00:02.0 reg 1c 32bit mmio: [ffd40000, ffd7ffff]
[    0.556753] PCI: 0000:00:02.1 reg 10 32bit mmio: [0, 7ffff]
[    0.556753] PCI: 0000:00:1b.0 reg 10 64bit mmio: [0, 3fff]
[    0.556753] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.556753] pci 0000:00:1b.0: PME# disabled
[    0.556753] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.556753] pci 0000:00:1c.0: PME# disabled
[    0.556753] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.556753] pci 0000:00:1c.2: PME# disabled
[    0.556753] PCI: 0000:00:1d.0 reg 20 io port: [afe0, afff]
[    0.556753] PCI: 0000:00:1d.1 reg 20 io port: [af80, af9f]
[    0.556753] PCI: 0000:00:1d.2 reg 20 io port: [af60, af7f]
[    0.556753] PCI: 0000:00:1d.3 reg 20 io port: [af40, af5f]
[    0.556780] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffd3fc00, ffd3ffff]
[    0.556838] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.556844] pci 0000:00:1d.7: PME# disabled
[    0.557002] pci 0000:00:1f.0: quirk: region d800-d87f claimed by ICH6 ACPI/GPIO/TCO
[    0.557007] pci 0000:00:1f.0: quirk: region eec0-eeff claimed by ICH6 GPIO
[    0.557037] PCI: 0000:00:1f.1 reg 10 io port: [af38, af3f]
[    0.557045] PCI: 0000:00:1f.1 reg 14 io port: [af34, af37]
[    0.557053] PCI: 0000:00:1f.1 reg 18 io port: [af28, af2f]
[    0.557062] PCI: 0000:00:1f.1 reg 1c io port: [af24, af27]
[    0.557070] PCI: 0000:00:1f.1 reg 20 io port: [af10, af1f]
[    0.557132] PCI: 0000:00:1f.2 reg 10 io port: [af08, af0f]
[    0.557141] PCI: 0000:00:1f.2 reg 14 io port: [af04, af07]
[    0.557149] PCI: 0000:00:1f.2 reg 18 io port: [aef8, aeff]
[    0.557157] PCI: 0000:00:1f.2 reg 1c io port: [aef4, aef7]
[    0.557166] PCI: 0000:00:1f.2 reg 20 io port: [aee0, aeef]
[    0.557174] PCI: 0000:00:1f.2 reg 24 32bit mmio: [ffd3f800, ffd3fbff]
[    0.557303] pci 0000:00:1f.2: PME# supported from D3hot
[    0.557308] pci 0000:00:1f.2: PME# disabled
[    0.557397] PCI: 0000:01:00.0 reg 10 32bit mmio: [ffce0000, ffcfffff]
[    0.557422] PCI: 0000:01:00.0 reg 18 io port: [bfe0, bfff]
[    0.557511] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.557519] pci 0000:01:00.0: PME# disabled
[    0.557570] PCI: bridge 0000:00:1c.0 io port: [b000, bfff]
[    0.557576] PCI: bridge 0000:00:1c.0 32bit mmio: [ffc00000, ffcfffff]
[    0.560077] PCI: 0000:02:00.0 reg 10 32bit mmio: [ffaff000, ffafffff]
[    0.560285] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.560299] pci 0000:02:00.0: PME# disabled
[    0.560353] PCI: bridge 0000:00:1c.2 32bit mmio: [ffa00000, ffafffff]
[    0.560428] PCI: 0000:03:0b.0 reg 10 32bit mmio: [0, fff]
[    0.560450] pci 0000:03:0b.0: supports D1
[    0.560452] pci 0000:03:0b.0: supports D2
[    0.560455] pci 0000:03:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.560461] pci 0000:03:0b.0: PME# disabled
[    0.560503] PCI: 0000:03:0b.1 reg 10 32bit mmio: [0, 7ff]
[    0.560513] PCI: 0000:03:0b.1 reg 14 32bit mmio: [0, 3fff]
[    0.560571] pci 0000:03:0b.1: supports D1
[    0.560573] pci 0000:03:0b.1: supports D2
[    0.560575] pci 0000:03:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.560581] pci 0000:03:0b.1: PME# disabled
[    0.560623] PCI: 0000:03:0b.2 reg 10 32bit mmio: [0, fff]
[    0.560687] pci 0000:03:0b.2: supports D1
[    0.560689] pci 0000:03:0b.2: supports D2
[    0.560691] pci 0000:03:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.560697] pci 0000:03:0b.2: PME# disabled
[    0.560736] PCI: 0000:03:0b.3 reg 10 32bit mmio: [0, ff]
[    0.560799] pci 0000:03:0b.3: supports D1
[    0.560801] pci 0000:03:0b.3: supports D2
[    0.560803] pci 0000:03:0b.3: PME# supported from D0 D1 D2 D3hot
[    0.560809] pci 0000:03:0b.3: PME# disabled
[    0.560855] pci 0000:00:1e.0: transparent bridge
[    0.560910] bus 00 -> node 0
[    0.560917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.561128] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.561293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.561440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[    0.564548] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.564548] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.564599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.564812] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.565026] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.565323] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.565537] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.568094] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.568384] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.568399] pnp: PnP ACPI init
[    0.568399] ACPI: bus type pnp registered
[    0.576986] pnp: PnP ACPI: found 13 devices
[    0.576989] ACPI: ACPI bus type pnp unregistered
[    0.576992] PnPBIOS: Disabled by ACPI PNP
[    0.577013] PCI: Using ACPI for IRQ routing
[    0.584041] NET: Registered protocol family 8
[    0.584044] NET: Registered protocol family 20
[    0.584066] NetLabel: Initializing
[    0.584066] NetLabel:  domain hash size = 128
[    0.584066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584075] NetLabel:  unlabeled traffic allowed by default
[    0.584084] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.584089] hpet0: 3 64-bit timers, 14318180 Hz
[    0.585684] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.585687]    actual entries 65620
[    0.585780] AppArmor: AppArmor Filesystem Enabled
[    0.585808] ACPI: RTC can wake from S4
[    0.588044] Switched to high resolution mode on CPU 0
[    0.588599] Switched to high resolution mode on CPU 1
[    0.592025] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.592028] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.592032] system 00:00: iomem range 0x100000-0x3f74ffff could not be reserved
[    0.592036] system 00:00: iomem range 0x3f750000-0x3f75ffff could not be reserved
[    0.592040] system 00:00: iomem range 0x3f760000-0x3f7fffff could not be reserved
[    0.592043] system 00:00: iomem range 0x3f800000-0x3fffffff could not be reserved
[    0.592047] system 00:00: iomem range 0xfec00000-0xfec17fff could not be reserved
[    0.592051] system 00:00: iomem range 0xfec20000-0xfec27fff could not be reserved
[    0.592054] system 00:00: iomem range 0xfed14000-0xfed19fff could not be reserved
[    0.592058] system 00:00: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.592062] system 00:00: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.592065] system 00:00: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.592069] system 00:00: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    0.592073] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.592076] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.592080] system 00:00: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.592087] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.592100] system 00:09: ioport range 0x1e0-0x1ef has been reserved
[    0.592103] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.592107] system 00:09: ioport range 0xe000-0xe07f has been reserved
[    0.592110] system 00:09: ioport range 0xe080-0xe0ff has been reserved
[    0.592114] system 00:09: ioport range 0xe400-0xe47f has been reserved
[    0.592117] system 00:09: ioport range 0xe480-0xe4ff has been reserved
[    0.592120] system 00:09: ioport range 0xe800-0xe87f has been reserved
[    0.592124] system 00:09: ioport range 0xe880-0xe8ff has been reserved
[    0.592127] system 00:09: ioport range 0xec00-0xec7f has been reserved
[    0.592131] system 00:09: ioport range 0xec80-0xecff has been reserved
[    0.592134] system 00:09: ioport range 0xd800-0xd87f has been reserved
[    0.592138] system 00:09: ioport range 0xd880-0xd89f has been reserved
[    0.592141] system 00:09: ioport range 0xeeb0-0xeebf has been reserved
[    0.592145] system 00:09: ioport range 0xeec0-0xeeff has been reserved
[    0.592148] system 00:09: ioport range 0x690-0x6ff has been reserved
[    0.592155] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.627422] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.627427] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.627434] pci 0000:00:1c.0:   MEM window: 0xffc00000-0xffcfffff
[    0.627440] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.627448] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.627451] pci 0000:00:1c.2:   IO window: disabled
[    0.627458] pci 0000:00:1c.2:   MEM window: 0xffa00000-0xffafffff
[    0.627463] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.627494] pci 0000:03:0b.0: CardBus bridge, secondary bus 0000:04
[    0.627497] pci 0000:03:0b.0:   IO window: 0x001000-0x0010ff
[    0.627503] pci 0000:03:0b.0:   IO window: 0x001400-0x0014ff
[    0.627510] pci 0000:03:0b.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.627516] pci 0000:03:0b.0:   MEM window: 0x54000000-0x57ffffff
[    0.627522] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.627526] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.627533] pci 0000:00:1e.0:   MEM window: 0x54000000-0x59ffffff
[    0.627539] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.627559] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.627565] pci 0000:00:1c.0: setting latency timer to 64
[    0.627576] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.627581] pci 0000:00:1c.2: setting latency timer to 64
[    0.627590] pci 0000:00:1e.0: setting latency timer to 64
[    0.627601] pci 0000:03:0b.0: enabling device (0000 -> 0003)
[    0.627606] pci 0000:03:0b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.627615] bus: 00 index 0 io port: [0, ffff]
[    0.627618] bus: 00 index 1 mmio: [0, ffffffff]
[    0.627621] bus: 01 index 0 io port: [b000, bfff]
[    0.627623] bus: 01 index 1 mmio: [ffc00000, ffcfffff]
[    0.627626] bus: 01 index 2 mmio: [0, 0]
[    0.627628] bus: 01 index 3 mmio: [0, 0]
[    0.627630] bus: 02 index 0 mmio: [0, 0]
[    0.627633] bus: 02 index 1 mmio: [ffa00000, ffafffff]
[    0.627635] bus: 02 index 2 mmio: [0, 0]
[    0.627638] bus: 02 index 3 mmio: [0, 0]
[    0.627640] bus: 03 index 0 io port: [1000, 1fff]
[    0.627643] bus: 03 index 1 mmio: [54000000, 59ffffff]
[    0.627646] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    0.627648] bus: 03 index 3 io port: [0, ffff]
[    0.627651] bus: 03 index 4 mmio: [0, ffffffff]
[    0.627653] bus: 04 index 0 io port: [1000, 10ff]
[    0.627656] bus: 04 index 1 io port: [1400, 14ff]
[    0.627658] bus: 04 index 2 mmio: [50000000, 53ffffff]
[    0.627661] bus: 04 index 3 mmio: [54000000, 57ffffff]
[    0.627671] NET: Registered protocol family 2
[    0.640057] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.640315] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.640828] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.641108] TCP: Hash tables configured (established 131072 bind 65536)
[    0.641112] TCP reno registered
[    0.648098] NET: Registered protocol family 1
[    0.648235] checking if image is initramfs... it is
[    1.415995] Freeing initrd memory: 8011k freed
[    1.416417] Simple Boot Flag value 0xb read from CMOS RAM was invalid
[    1.416421] Simple Boot Flag at 0x7c set to 0x1
[    1.417409] audit: initializing netlink socket (disabled)
[    1.417438] type=2000 audit(1230076997.416:1): initialized
[    1.424237] highmem bounce pool size: 64 pages
[    1.424244] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.427221] VFS: Disk quotas dquot_6.5.1
[    1.427328] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.427454] msgmni has been set to 1762
[    1.427594] io scheduler noop registered
[    1.427598] io scheduler anticipatory registered
[    1.427600] io scheduler deadline registered
[    1.427614] io scheduler cfq registered (default)
[    1.427629] pci 0000:00:02.0: Boot video device
[    1.427863] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.427913] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.427965] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.428022] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.428145] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.428192] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.428240] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.428290] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.428672] isapnp: Scanning for PnP cards...
[    1.782374] isapnp: No Plug & Play device found
[    1.823755] hpet_resources: 0xfed00000 is busy
[    1.823851] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.824830] 00:0c: ttyS0 at I/O 0x338 (irq = 4) is a 16550A
[    1.826845] brd: module loaded
[    1.826929] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.827071] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.831940] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.831948] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.832446] mice: PS/2 mouse device common for all mice
[    1.832598] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.832631] rtc0: alarms up to one year, hpet irqs
[    1.832779] EISA: Probing bus 0 at eisa.0
[    1.832786] Cannot allocate resource for EISA slot 1
[    1.832817] EISA: Detected 0 cards.
[    1.832821] cpuidle: using governor ladder
[    1.832824] cpuidle: using governor menu
[    1.833402] TCP cubic registered
[    1.833434] Using IPI No-Shortcut mode
[    1.833651] registered taskstats version 1
[    1.833801]   Magic number: 4:350:52
[    1.833909] rtc_cmos 00:08: setting system clock to 2008-12-24 00:03:18 UTC (1230076998)
[    1.833913] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.833916] EDD information not available.
[    1.834178] Freeing unused kernel memory: 424k freed
[    1.834230] Write protecting the kernel text: 2576k
[    1.834262] Write protecting the kernel read-only data: 936k
[    1.851668] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.033159] fuse init (API version 7.9)
[    2.081267] ACPI: SSDT 3F7553C0, 00F3 (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    2.081622] ACPI: SSDT 3F755529, 034E (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    2.082255] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.082318] processor ACPI0007:00: registered as cooling_device0
[    2.082437] ACPI: SSDT 3F7554B3, 0076 (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    2.082750] ACPI: SSDT 3F755877, 0079 (r2 TOSHIB A003C    20060907 MSFT  100000E)
[    2.083399] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.083456] processor ACPI0007:01: registered as cooling_device1
[    2.086198] thermal LNXTHERM:01: registered as thermal_zone0
[    2.086359] ACPI: Thermal Zone [THRM] (43 C)
[    2.097020] Marking TSC unstable due to TSC halts in idle
[    2.385082] ACPI: ACPI Dock Station Driver
[    2.519978] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.519982] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.520045] e1000e 0000:01:00.0: Disabling L1 ASPM
[    2.520073] e1000e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.520088] e1000e 0000:01:00.0: setting latency timer to 64
[    2.557486] usbcore: registered new interface driver usbfs
[    2.557514] usbcore: registered new interface driver hub
[    2.557562] usbcore: registered new device driver usb
[    2.559944] USB Universal Host Controller Interface driver v3.0
[    2.579455] 0000:01:00.0: 0000:01:00.0: Warning: detected ASPM enabled in EEPROM
[    2.626761] SCSI subsystem initialized
[    2.640300] 0000:01:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:0e:7b:80:3d:e5
[    2.640304] 0000:01:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.640382] 0000:01:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    2.640460] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.640471] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.640476] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.640522] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.640562] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000afe0
[    2.640747] usb usb1: configuration #1 chosen from 1 choice
[    2.640780] hub 1-0:1.0: USB hub found
[    2.640788] hub 1-0:1.0: 2 ports detected
[    2.670940] libata version 3.00 loaded.
[    2.744371] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.744384] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.744388] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.744420] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.744460] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000af80
[    2.744572] usb usb2: configuration #1 chosen from 1 choice
[    2.744604] hub 2-0:1.0: USB hub found
[    2.744612] hub 2-0:1.0: 2 ports detected
[    2.952372] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.952385] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.952390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.952419] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.952462] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000af60
[    2.952582] usb usb3: configuration #1 chosen from 1 choice
[    2.952613] hub 3-0:1.0: USB hub found
[    2.952622] hub 3-0:1.0: 2 ports detected
[    3.056518] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.056529] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.056534] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.056562] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.056601] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000af40
[    3.056705] usb usb4: configuration #1 chosen from 1 choice
[    3.056736] hub 4-0:1.0: USB hub found
[    3.056743] hub 4-0:1.0: 2 ports detected
[    3.064121] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.160589] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.160606] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.160610] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.160636] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.164541] ehci_hcd 0000:00:1d.7: debug port 1
[    3.164549] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.164558] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffd3fc00
[    3.188479] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.188683] usb usb5: configuration #1 chosen from 1 choice
[    3.188716] hub 5-0:1.0: USB hub found
[    3.188726] hub 5-0:1.0: 8 ports detected
[    3.396602] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.396639] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.396655] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.396688] ohci1394 0000:03:0b.1: enabling device (0000 -> 0002)
[    3.396698] ohci1394 0000:03:0b.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.409038] ahci 0000:00:1f.2: version 3.0
[    3.409050] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.409148] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    3.409153] ahci 0000:00:1f.2: flags: 64bit ncq ilck pm led clo pio slum part 
[    3.409159] ahci 0000:00:1f.2: setting latency timer to 64
[    3.421058] scsi0 : ahci
[    3.421173] scsi1 : ahci
[    3.421252] scsi2 : ahci
[    3.421328] scsi3 : ahci
[    3.422663] ata1: SATA max UDMA/133 abar m1024@0xffd3f800 port 0xffd3f900 irq 221
[    3.422667] ata2: DUMMY
[    3.422670] ata3: SATA max UDMA/133 abar m1024@0xffd3f800 port 0xffd3fa00 irq 221
[    3.422673] ata4: DUMMY
[    3.446437] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[58006000-580067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.500120] Clocksource tsc unstable (delta = -300144563 ns)
[    3.584269] usb 2-1: device not accepting address 2, error -71
[    3.640152] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.740147] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.741510] ata1.00: ATA-7: HTS541010G9SA00, MBZOC60D, max UDMA/100
[    3.741513] ata1.00: 195371568 sectors, multi 0: LBA48 NCQ (not used)
[    3.743102] ata1.00: configured for UDMA/100
[    4.076143] ata3: SATA link down (SStatus 0 SControl 300)
[    4.092332] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9SA00  MBZO PQ: 0 ANSI: 5
[    4.101964] ata_piix 0000:00:1f.1: version 2.12
[    4.101979] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.102022] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.102114] scsi4 : ata_piix
[    4.102214] scsi5 : ata_piix
[    4.103125] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xaf10 irq 14
[    4.103129] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xaf18 irq 15
[    4.113382] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.116046] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    4.125772] Driver 'sd' needs updating - please use bus_type methods
[    4.126573] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.126604] sd 0:0:0:0: [sda] Write Protect is off
[    4.126607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.126648] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.126744] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.126767] sd 0:0:0:0: [sda] Write Protect is off
[    4.126770] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.126811] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.126816]  sda:<6>ata5.00: ATAPI: MATSHITADVD-RAM UJ-842S, 1.01, max UDMA/33
[    4.280598] ata5.00: configured for UDMA/33
[    4.280685] ata6: port disabled. ignoring.
[    4.282688] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-842S  1.01 PQ: 0 ANSI: 5
[    4.282877] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    4.288645] usb 2-1: configuration #1 chosen from 1 choice
[    4.302811] Driver 'sr' needs updating - please use bus_type methods
[    4.502177]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    4.556082] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.563804] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.563809] Uniform CD-ROM driver Revision: 3.20
[    4.563901] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.718044] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000a37e7b]
[    5.070211] PM: Starting manual resume from disk
[    5.070215] PM: Resume from partition 8:5
[    5.070217] PM: Checking hibernation image.
[    5.070424] PM: Resume from disk failed.
[    5.089455] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.089459] EXT3-fs: write access will be enabled during recovery.
[    8.088256] kjournald starting.  Commit interval 5 seconds
[    8.088279] EXT3-fs: sda7: orphan cleanup on readonly fs
[    8.088285] ext3_orphan_cleanup: deleting unreferenced inode 404653
[    8.088325] EXT3-fs: sda7: 1 orphan inode deleted
[    8.088328] EXT3-fs: recovery complete.
[    8.111852] EXT3-fs: mounted filesystem with ordered data mode.
[   15.351023] udevd version 124 started
[   15.916910] iTCO_vendor_support: vendor-support=0
[   16.074770] Linux agpgart interface v0.103
[   16.174651] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   16.175199] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   16.191996] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   16.266908] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.348132] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.397682] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   16.399825] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0xd860)
[   16.399956] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.730685] ACPI: AC Adapter [ADP1] (on-line)
[   16.822195] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.840158] ACPI: Power Button (FF) [PWRF]
[   16.840308] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   16.840390] ACPI: Lid Switch [LID]
[   16.840478] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   16.872037] ACPI: Power Button (CM) [PWRB]
[   16.873224] ACPI: Battery Slot [BAT1] (battery present)
[   16.873286] ACPI: Battery Slot [BAT2] (battery absent)
[   17.095393] Yenta: CardBus bridge found at 0000:03:0b.0 [1179:0001]
[   17.095417] Yenta: Enabling burst memory read transactions
[   17.095423] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.095426] Yenta: Routing CardBus interrupts to PCI
[   17.095432] Yenta TI: socket 0000:03:0b.0, mfunc 0x01aa1022, devctl 0x64
[   17.117985] sdhci: Secure Digital Host Controller Interface driver
[   17.117990] sdhci: Copyright(c) Pierre Ossman
[   17.184198] acpi device:0d: registered as cooling_device2
[   17.184443] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/input/input5
[   17.204594] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: found ejectable bay
[   17.204600] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: Adding notify handler
[   17.204788] ACPI: Error installing bay notify handler
[   17.204826] ACPI: \_SB_.PCI0.FNC2.PRT2: found ejectable bay
[   17.204830] ACPI: \_SB_.PCI0.FNC2.PRT2: Adding notify handler
[   17.204849] ACPI: Error installing bay notify handler
[   17.216032] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   17.324830] Yenta: ISA IRQ mask 0x0cf8, PCI irq 21
[   17.324836] Socket status: 30000006
[   17.324840] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   17.324847] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   17.324850] cs: IO port probe 0x1000-0x1fff: clean.
[   17.325085] pcmcia: parent PCI bridge Memory window: 0x54000000 - 0x59ffffff
[   17.325088] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   17.331449] tifm_7xx1 0000:03:0b.2: enabling device (0000 -> 0002)
[   17.331458] tifm_7xx1 0000:03:0b.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   17.331559] sdhci-pci 0000:03:0b.3: SDHCI controller found [104c:803c] (rev 0)
[   17.331575] sdhci-pci 0000:03:0b.3: enabling device (0000 -> 0002)
[   17.331580] sdhci-pci 0000:03:0b.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   17.331648] mmc0: SDHCI controller on PCI [0000:03:0b.3] using DMA
[   17.335077] intel_rng: FWH not detected
[   17.346203] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: found ejectable bay
[   17.346209] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: Adding notify handler
[   17.346243] ACPI: Error installing bay notify handler
[   17.346275] ACPI: \_SB_.PCI0.FNC2.PRT2: found ejectable bay
[   17.346278] ACPI: \_SB_.PCI0.FNC2.PRT2: Adding notify handler
[   17.346297] ACPI: Error installing bay notify handler
[   17.437436] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   17.439220] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   17.439275] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x680, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   17.748072] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.748077] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   17.748704] iwl3945 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.748720] iwl3945 0000:02:00.0: setting latency timer to 64
[   17.748744] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.843156] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.844989] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.131279] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   18.186056] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   18.331173] iwl3945 0000:02:00.0: PCI INT A disabled
[   18.572602] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   18.572612] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   18.572624] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.572658] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.792603] cs: IO port probe 0x100-0x3af: clean.
[   18.794486] cs: IO port probe 0x3e0-0x4ff: clean.
[   18.795266] cs: IO port probe 0x820-0x8ff: clean.
[   18.795952] cs: IO port probe 0xc00-0xcf7: clean.
[   18.796862] cs: IO port probe 0xa00-0xaff: clean.
[   19.381602] lp: driver loaded but no devices found
[   19.578212] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k
[   20.125871] EXT3 FS on sda7, internal journal

[   20.903642] kjournald starting.  Commit interval 5 seconds
[   20.904070] EXT3 FS on sda6, internal journal
[   20.904080] EXT3-fs: mounted filesystem with ordered data mode.
[   21.067421] type=1505 audit(1230095017.846:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4283
[   21.270484] type=1505 audit(1230095018.050:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4288
[   21.270702] type=1505 audit(1230095018.050:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4288
[   21.451998] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.460223] toshiba_acpi: Toshiba Laptop ACPI Extras version experimental-dev-toshiba-test-5
[   22.460228] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   22.480137] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: found ejectable bay
[   22.480143] ACPI: \_SB_.PCI0.FNC1.IDE0.HD_0: Adding notify handler
[   22.480189] ACPI: Error installing bay notify handler
[   22.480854] ACPI: \_SB_.PCI0.FNC2.PRT2: found ejectable bay
[   22.480859] ACPI: \_SB_.PCI0.FNC2.PRT2: Adding notify handler
[   22.480879] ACPI: Error installing bay notify handler
[   22.579640] ACPI: WMI: Mapper loaded
[   23.486453] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.557956] apm: BIOS not found.
[   23.706096] ppdev: user-space parallel port driver
[   25.733381] Bluetooth: Core ver 2.13
[   25.733584] NET: Registered protocol family 31
[   25.733592] Bluetooth: HCI device and connection manager initialized
[   25.733602] Bluetooth: HCI socket layer initialized
[   25.760143] Bluetooth: L2CAP ver 2.11
[   25.760154] Bluetooth: L2CAP socket layer initialized
[   25.779313] Bluetooth: SCO (Voice Link) ver 0.6
[   25.779324] Bluetooth: SCO socket layer initialized
[   25.794561] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.794576] Bluetooth: BNEP filters: protocol multicast
[   25.859174] Bridge firewalling registered
[   25.859446] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   25.883481] Bluetooth: RFCOMM socket layer initialized
[   25.883508] Bluetooth: RFCOMM TTY layer initialized
[   25.883512] Bluetooth: RFCOMM ver 1.10
[   30.181583] iwl3945 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   30.181749] iwl3945 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   30.186028] firmware: requesting iwlwifi-3945-1.ucode
[   30.319444] Registered led device: iwl-phy0:radio
[   30.319535] Registered led device: iwl-phy0:assoc
[   30.319571] Registered led device: iwl-phy0:RX
[   30.319604] Registered led device: iwl-phy0:TX
[   30.418971] [drm] Initialized drm 1.1.0 20060810
[   30.424920] pci 0000:00:02.0: power state changed by ACPI to D0
[   30.424938] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.424943] pci 0000:00:02.0: setting latency timer to 64
[   30.425145] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.445973] NET: Registered protocol family 17
[   31.794707] 0000:01:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   31.794715] 0000:01:00.0: eth0: 10/100 speed: disabling TSO
[   86.837297] CPU0 attaching NULL sched-domain.
[   86.837310] CPU1 attaching NULL sched-domain.
[   86.848083] CPU0 attaching sched-domain:
[   86.848091]  domain 0: span 0-1 level MC
[   86.848095]   groups: 0 1
[   86.848104] CPU1 attaching sched-domain:
[   86.848108]  domain 0: span 0-1 level MC
[   86.848114]   groups: 1 0
[  154.717985] NET: Registered protocol family 10
[  154.719052] lo: Disabled Privacy Extensions
[  154.722724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  165.356018] eth0: no IPv6 routers present
[  421.232080] CE: hpet increasing min_delta_ns to 15000 nsec[/HTML]

---

### Post by balaknair on 2008-12-24
I had a similar issue with Intrepid(dual booting with XP, which also crashed often).
XP also being affected led me to think it might be a hardware error. Turned out to be a faulty power supply unit, which had buggered my GPU and mobo. Changing the PSU fixed the issue partly, but at 1280x1024 resolution(the max my monitor supports) the display would flicker and occasionally the OS would crash. Setting the resolution to 1152x864 makes everything return to normal in both XP and Intrepid. Guess my graphics card didn't survive unscathed.

---

### Post by todlangweilig on 2008-12-24
I'm not sure how applicable this is in my situation, since I have a laptop. I don't want to buy a new PSU until I have some more evidence that it is the culprit. 

I haven't noticed any crashing in Windows, I rarely use it however.

---

### Post by todlangweilig on 2008-12-26
bump

---

### Post by 2hot6ft2 on 2008-12-29
Don't know if this will help or not but it's worth a look.
System Freezes
Ubunut Intrepid - Clocksource From Hell
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell)

Ubuntu Intrepid - Clocksource Fixed, System Still Hangs, AND No Videos - FGRLX Fixes It
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)

---

### Post by todlangweilig on 2008-12-30
Thanks for the links. I don't think the second link applies, I don't have ATI graphics. I think it's an onboard Intel graphics chip. 

I'll give the first link a try if my computer freezes again. I did have something in the logs about "hpet," but only the numbers 15000ns and 22500ns. The computer hasn't frozen it lately. It's so frustrating that it's intermittent. 

Could this have anything to do with the problem?
apm: BIOS not found.
ACPI: Error installing bay notify handler

Thank you guys for your help, please keep the ideas coming.

---

### Post by Guilden_NL on 2009-04-08
Dank u wel 2hot!
I've been searching for a solution since the Intrepid upgrade to my HP HDX18 and this was the only post that made sense.  I tried a few of the others, but they didn't work, as I suspected they wouldn't.  
This one made sense, and _**it worked!**_ =D>

---

