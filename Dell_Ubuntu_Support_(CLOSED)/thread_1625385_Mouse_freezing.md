---
title: "Mouse freezing"
date: 2010-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Paham on 2010-11-19
Hi All,

I'm  new to linux/ubuntu and am new to this forum. I just installed the latest 32bit release on my Dell E521. However, there is one issue, my mouse freezes after 5 to 15 minutes of use. 

The only way to gain control back is to reboot. My kb works fine.

Any ideas? Thank you so much for your time.

---

### Post by azertyh on 2010-11-19
hello,
check your syslog and dmesg. open a terminal and type
```
tail -f /var/log/syslog
```
(CTRL+C to stop it)
```
dmesg
```
sometimes, you can find in these 2 files what is wrong. then google this message. or post it here.

---

### Post by kurt-ub on 2010-12-20
Hi,

I'm exactly like Paham: new to linux, with ubuntu 10.10 freshly installed, and with only one issue, my mouse freezing after few to several minutes of use.

Here, some informations about my computer:
DELL E521 AMD Athlon (tm) 64 X2 4200+
Ubuntu 10.10 (maverick)
kernel Linux 2.6.35-23
GNOME 2.32.0
BIOS 0x01ED 1.0.3
USB classical mouse (no PS/2 input possible)

What I observe is that:
- the mouse (and only the mouse not the keyboard) freezes randomly (?) after 1 to 30 minutes. It is not linked to the time used or the distance
- the mouse (contrary to what I have read) stay frozen even after an unplug/plug
- it is not related to the type (wireless or not, optical or not) or brand of mouse (dell, microsoft and razer)

I've done some research, and it seems that this is specific to dell system (especially E521) and possibly linked to some bios issue. It may also be linked to the type of host controller ohci (not ok) or ehci (ok).

Some solutions have been proposed, but either it doesn't work or I dont know how to do it
- upgrade bios seems to work for some people[INDENT]        -->didnt try because I cant find my bios version  on [http://linux.dell.com/repo/firmware/bios-hdrs](http://linux.dell.com/repo/firmware/bios-hdrs)
[/INDENT][INDENT]        --> I think I found it on _[COLOR=Blue][dell support]("http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R136403&formatcnt=0&libid=0&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=181780")[/COLOR]_ but it is a windows version and I dont know how to use it on linux
[/INDENT]-  use usb hub passive/active[INDENT]         --> it seems that my mouse stays active a little longer but it doesnt solve the problem at the end
[/INDENT]- add a kernel argument at the boot line (see here [http://ubuntuforums.org/showthread.php?t=279626&page=9]("http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R136403&formatcnt=0&libid=0&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=181780")): 
```
title           Debian GNU/Linux, kernel 2.6.20-1-amd64
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-1-amd64 root=/dev/sda1 ro noapic irqpoll pci=routeirq
initrd          /boot/initrd.img-2.6.20-1-amd64
savedefault

title           Debian GNU/Linux, kernel 2.6.20-1-amd64 (single-user mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-1-amd64 root=/dev/sda1 ro noapic irqpoll pci=routeirq single
initrd          /boot/initrd.img-2.6.20-1-amd64
```[INDENT]--> but I dont know how to do that.
[/INDENT]Finally, here the results of syslog command

```
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   period_event : 0
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   start_threshold  : -1
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   stop_threshold   : 1444937728
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   silence_threshold: 0
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   silence_size : 0
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   boundary     : 1444937728
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   appl_ptr     : 87364
Dec 20 12:37:05 quentin-DELL pulseaudio[1580]: alsa-util.c:   hw_ptr       : 87364
Dec 20 12:37:31 quentin-DELL kernel: [   90.169026] Clocksource tsc unstable (delta = -218769561 ns)
Dec 20 12:37:40 quentin-DELL kernel: [   98.904854] ppdev: user-space parallel port driver

```and dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 003FF00000 mask FFFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  modified: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  modified: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  modified: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f3cb0] f3cb0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 2f526000 - 2ff68000
[    0.000000] ACPI: RSDP 000f83c0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 3fee3040 00040 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 3fee3100 00074 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 3fee31c0 0592F (v01 DELL   AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3fee0000 00040
[    0.000000] ACPI: BOOT 3fee8b40 00028 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 3fee8c80 00206 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 3fee8f00 00038 (v01 DELL    bMk     42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 3fee8f80 0003C (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: SLIC 3fee9000 00176 (v01 DELL    bMk     42302E31 AWRD 0100000E)
[    0.000000] ACPI: APIC 3fee8bc0 00072 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 134MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fee0
[    0.000000] On node 0 totalpages: 261744
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 270 pages used for memmap
[    0.000000]   HighMem zone: 34260 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3ff00000 (gap: 3ff00000:b0100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259698
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=7f60b0ae-9299-4dca-84dc-f4c18ec23264 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5237100 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [002f526000 - 002ff68000]         RAMDISK
[    0.000000]   #4 [00009a1000 - 00009a41cc]             BRK
[    0.000000]   #5 [00000f3cc0 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000f3cb0 - 00000f3cc0]    MP-table mpf
[    0.000000]   #7 [000009f000 - 00000f2124]   BIOS reserved
[    0.000000]   #8 [00000f2260 - 00000f3cb0]   BIOS reserved
[    0.000000]   #9 [00000f2124 - 00000f2260]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
[    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
[    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
[    0.000000]   #17 [0001801100 - 0001801154]         BOOTMEM
[    0.000000]   #18 [0001801180 - 0001804180]         BOOTMEM
[    0.000000]   #19 [0001804180 - 0001804190]         BOOTMEM
[    0.000000]   #20 [00018041c0 - 0001804dc0]         BOOTMEM
[    0.000000]   #21 [0001804dc0 - 0001804de5]         BOOTMEM
[    0.000000]   #22 [0001804e00 - 0001804e27]         BOOTMEM
[    0.000000]   #23 [0001804e40 - 0001804f90]         BOOTMEM
[    0.000000]   #24 [0001804fc0 - 0001805000]         BOOTMEM
[    0.000000]   #25 [0001805000 - 0001805040]         BOOTMEM
[    0.000000]   #26 [0001805040 - 0001805080]         BOOTMEM
[    0.000000]   #27 [0001805080 - 00018050c0]         BOOTMEM
[    0.000000]   #28 [00018050c0 - 0001805100]         BOOTMEM
[    0.000000]   #29 [0001805100 - 0001805140]         BOOTMEM
[    0.000000]   #30 [0001805140 - 0001805180]         BOOTMEM
[    0.000000]   #31 [0001805180 - 00018051c0]         BOOTMEM
[    0.000000]   #32 [00018051c0 - 0001805200]         BOOTMEM
[    0.000000]   #33 [0001805200 - 0001805210]         BOOTMEM
[    0.000000]   #34 [0001805240 - 0001805250]         BOOTMEM
[    0.000000]   #35 [0001805280 - 00018052ea]         BOOTMEM
[    0.000000]   #36 [0001805300 - 000180536a]         BOOTMEM
[    0.000000]   #37 [0001c00000 - 0001c0e000]         BOOTMEM
[    0.000000]   #38 [0001e00000 - 0001e0e000]         BOOTMEM
[    0.000000]   #39 [0001807380 - 0001807384]         BOOTMEM
[    0.000000]   #40 [00018073c0 - 00018073c4]         BOOTMEM
[    0.000000]   #41 [0001807400 - 0001807408]         BOOTMEM
[    0.000000]   #42 [0001807440 - 0001807448]         BOOTMEM
[    0.000000]   #43 [0001807480 - 0001807528]         BOOTMEM
[    0.000000]   #44 [0001807540 - 00018075a8]         BOOTMEM
[    0.000000]   #45 [00018075c0 - 000180b5c0]         BOOTMEM
[    0.000000]   #46 [000180b5c0 - 000188b5c0]         BOOTMEM
[    0.000000]   #47 [000188b5c0 - 00018cb5c0]         BOOTMEM
[    0.000000]   #48 [0001e0e000 - 000230c96c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fee0)
[    0.000000] Memory: 1013360k/1047424k available (4930k kernel code, 33616k reserved, 2334k data, 684k init, 138120k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] HPET config register value = 0xFFFFFFFF. Disabling HPET
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2204.375 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4408.75 BogoMIPS (lpj=8817500)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004037] Security Framework initialized
[    0.004065] AppArmor: AppArmor initialized
[    0.004068] Yama: becoming mindful.
[    0.004141] Mount-cache hash table entries: 512
[    0.004307] Initializing cgroup subsys ns
[    0.004312] Initializing cgroup subsys cpuacct
[    0.004318] Initializing cgroup subsys memory
[    0.004329] Initializing cgroup subsys devices
[    0.004332] Initializing cgroup subsys freezer
[    0.004336] Initializing cgroup subsys net_cls
[    0.008006] CPU: Physical Processor ID: 0
[    0.008008] CPU: Processor Core ID: 0
[    0.008012] mce: CPU supports 5 MCE banks
[    0.008026] using C1E aware idle routine
[    0.008035] Performance Events: AMD PMU driver.
[    0.008045] ... version:                0
[    0.008047] ... bit width:              48
[    0.008050] ... generic registers:      4
[    0.008052] ... value mask:             0000ffffffffffff
[    0.008055] ... max period:             00007fffffffffff
[    0.008058] ... fixed-purpose events:   0
[    0.008060] ... event mask:             000000000000000f
[    0.010862] ACPI: Core revision 20100428
[    0.020010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020015] ftrace: allocating 21766 entries in 43 pages
[    0.024110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024647] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.032000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.032000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.032000] ..... (found apic 0 pin 0) ...
[    0.040000] ....... failed.
[    0.040000] ...trying to set up timer as Virtual Wire IRQ...
[    0.040000] ..... failed.
[    0.040000] ...trying to set up timer as ExtINT IRQ...
[    0.081343] ..... works.
[    0.081345] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.084000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.168054] Brought up 2 CPUs
[    0.168057] Total of 2 processors activated (8818.25 BogoMIPS).
[    0.168335] devtmpfs: initialized
[    0.168968] regulator: core version 0.5
[    0.169002] Time: 11:35:00  Date: 12/20/10
[    0.169049] NET: Registered protocol family 16
[    0.169185] EISA bus registered
[    0.169190] node 0 link 0: io port [8000, ffff]
[    0.169194] TOM: 0000000040000000 aka 1024M
[    0.169197] node 0 link 0: mmio [a0000, bffff]
[    0.169200] node 0 link 0: mmio [40000000, efffffff]
[    0.169203] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.169206] node 0 link 0: mmio [f0000000, f04fffff]
[    0.169210] bus: [00, 04] on node 0 link 0
[    0.169213] bus: 00 index 0 [io  0x0000-0xffff]
[    0.169215] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.169218] bus: 00 index 2 [mem 0x40000000-0xf3ffffff]
[    0.169220] bus: 00 index 3 [mem 0xf4000000-0xffffffff]
[    0.169228] ACPI: bus type pci registered
[    0.169302] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.169306] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in E820
[    0.169310] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
[    0.169312] PCI: Using MMCONFIG for extended config space
[    0.169314] PCI: Using configuration type 1 for base access
[    0.170299] Trying to unpack rootfs image as initramfs...
[    0.170299] bio: create slab <bio-0> at 0
[    0.172664] ACPI: EC: Look up EC in DSDT
[    0.178120] ACPI: Interpreter enabled
[    0.178123] ACPI: (supports S0 S1 S3 S4 S5)
[    0.178150] ACPI: Using IOAPIC for interrupt routing
[    0.186775] ACPI: No dock devices found.
[    0.186780] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.187738] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
[    0.189671] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
[    0.189674] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
[    0.189676] pci_root PNP0A08:00: host bridge window [io  0x8000-0xffff] (ignored)
[    0.189679] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
[    0.189682] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.189685] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xefffffff] (ignored)
[    0.189688] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
[    0.189691] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
[    0.189693] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
[    0.189913] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.189916] pci 0000:00:02.0: PME# disabled
[    0.189946] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.189949] pci 0000:00:03.0: PME# disabled
[    0.189978] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.189980] pci 0000:00:04.0: PME# disabled
[    0.190160] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.190198] pci 0000:00:0a.1: reg 20: [io  0x1c00-0x1c3f]
[    0.190203] pci 0000:00:0a.1: reg 24: [io  0x1c40-0x1c7f]
[    0.190227] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.190232] pci 0000:00:0a.1: PME# disabled
[    0.190295] pci 0000:00:0b.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
[    0.190323] pci 0000:00:0b.0: supports D1 D2
[    0.190325] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190329] pci 0000:00:0b.0: PME# disabled
[    0.190350] pci 0000:00:0b.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
[    0.190379] pci 0000:00:0b.1: supports D1 D2
[    0.190381] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190385] pci 0000:00:0b.1: PME# disabled
[    0.190416] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
[    0.190421] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.190425] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
[    0.190430] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
[    0.190434] pci 0000:00:0e.0: reg 20: [io  0xe000-0xe00f]
[    0.190439] pci 0000:00:0e.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
[    0.190480] pci 0000:00:0f.0: reg 10: [io  0x09e0-0x09e7]
[    0.190484] pci 0000:00:0f.0: reg 14: [io  0x0be0-0x0be3]
[    0.190489] pci 0000:00:0f.0: reg 18: [io  0x0960-0x0967]
[    0.190493] pci 0000:00:0f.0: reg 1c: [io  0x0b60-0x0b63]
[    0.190498] pci 0000:00:0f.0: reg 20: [io  0xcc00-0xcc0f]
[    0.190503] pci 0000:00:0f.0: reg 24: [mem 0xfe02c000-0xfe02cfff]
[    0.190579] pci 0000:00:10.1: reg 10: [mem 0xfe024000-0xfe027fff]
[    0.190612] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.190615] pci 0000:00:10.1: PME# disabled
[    0.190709] PCI: peer root bus 00 res updated from pci conf
[    0.190733] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.190737] pci 0000:00:02.0:   bridge window [io  0xa000-0xafff]
[    0.190740] pci 0000:00:02.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.190745] pci 0000:00:02.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.190766] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.190770] pci 0000:00:03.0:   bridge window [io  0x8000-0x8fff]
[    0.190773] pci 0000:00:03.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.190777] pci 0000:00:03.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.190811] pci 0000:03:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.190818] pci 0000:03:00.0: reg 18: [mem 0xfddf0000-0xfddfffff 64bit]
[    0.190823] pci 0000:03:00.0: reg 20: [io  0xbc00-0xbcff]
[    0.190830] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.190843] pci 0000:03:00.0: supports D1 D2
[    0.190865] pci 0000:03:00.1: reg 10: [mem 0xfdde0000-0xfddeffff 64bit]
[    0.190888] pci 0000:03:00.1: supports D1 D2
[    0.190899] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.190907] pci 0000:00:04.0: PCI bridge to [bus 03-03]
[    0.190911] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.190914] pci 0000:00:04.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.190918] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.190960] pci 0000:04:07.0: reg 10: [mem 0xfdcfe000-0xfdcfffff]
[    0.190994] pci 0000:04:07.0: supports D1 D2
[    0.190997] pci 0000:04:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191000] pci 0000:04:07.0: PME# disabled
[    0.191029] pci 0000:00:10.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.191033] pci 0000:00:10.0:   bridge window [io  0x9000-0x9fff]
[    0.191036] pci 0000:00:10.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.191040] pci 0000:00:10.0:   bridge window [mem 0xfdb00000-0xfdbfffff pref]
[    0.191043] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.191046] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.191049] pci 0000:00:10.0:   bridge window [mem 0x40000000-0xf3ffffff] (subtractive decode)
[    0.191051] pci 0000:00:10.0:   bridge window [mem 0xf4000000-0xffffffff] (subtractive decode)
[    0.191061] pci_bus 0000:00: on NUMA node 0
[    0.191066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.191294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.262995] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.263145] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.263293] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.263443] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[    0.263592] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[    0.263743] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.263893] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 *7 9 10 11 14 15)
[    0.264048] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.264200] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
[    0.264352] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.264503] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.264651] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.264800] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.264950] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
[    0.265098] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.265249] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.265399] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.265560] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.265711] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.265866] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.266063] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.266249] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.266434] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.266617] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.266800] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.266981] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.267167] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.267352] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.267537] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.267727] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.267913] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.268108] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.268293] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.268478] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.268664] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.268851] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.269040] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.269231] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.269419] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.269608] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.269793] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.269844] HEST: Table is not found!
[    0.269957] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.269961] vgaarb: loaded
[    0.270131] SCSI subsystem initialized
[    0.276060] libata version 3.00 loaded.
[    0.276107] usbcore: registered new interface driver usbfs
[    0.276120] usbcore: registered new interface driver hub
[    0.276146] usbcore: registered new device driver usb
[    0.276289] ACPI: WMI: Mapper loaded
[    0.276291] PCI: Using ACPI for IRQ routing
[    0.276296] PCI: pci_cache_line_size set to 64 bytes
[    0.276384] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.276387] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.276390] reserve RAM buffer: 000000003fee0000 - 000000003fffffff 
[    0.276496] NetLabel: Initializing
[    0.276498] NetLabel:  domain hash size = 128
[    0.276499] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.276514] NetLabel:  unlabeled traffic allowed by default
[    0.286845] AppArmor: AppArmor Filesystem Enabled
[    0.286867] pnp: PnP ACPI init
[    0.286891] ACPI: bus type pnp registered
[    0.291229] pnp: PnP ACPI: found 9 devices
[    0.291232] ACPI: ACPI bus type pnp unregistered
[    0.291235] PnPBIOS: Disabled by ACPI PNP
[    0.291249] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.291252] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.291255] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.291257] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.291260] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.291263] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.291266] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.291269] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.291273] system 00:01: [mem 0xfec80000-0xfecbffff] has been reserved
[    0.291276] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.291282] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.291285] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.291291] system 00:07: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.291296] system 00:08: [mem 0x000cf000-0x000cffff] has been reserved
[    0.291299] system 00:08: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.291302] system 00:08: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.291305] system 00:08: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.291308] system 00:08: [mem 0x3fee0000-0x3fefffff] could not be reserved
[    0.291311] system 00:08: [mem 0xffff0000-0xffffffff] has been reserved
[    0.291314] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.291317] system 00:08: [mem 0x00100000-0x3fedffff] could not be reserved
[    0.291320] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.291323] system 00:08: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.291326] system 00:08: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.291329] system 00:08: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.291332] system 00:08: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.291335] system 00:08: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.327313] Switching to clocksource acpi_pm
[    0.327453] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.327457] pci 0000:00:02.0:   bridge window [io  0xa000-0xafff]
[    0.327460] pci 0000:00:02.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.327464] pci 0000:00:02.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.327468] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.327471] pci 0000:00:03.0:   bridge window [io  0x8000-0x8fff]
[    0.327474] pci 0000:00:03.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.327477] pci 0000:00:03.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.327485] pci 0000:03:00.0: BAR 6: assigned [mem 0xfdd00000-0xfdd1ffff pref]
[    0.327488] pci 0000:00:04.0: PCI bridge to [bus 03-03]
[    0.327491] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.327494] pci 0000:00:04.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.327497] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.327501] pci 0000:00:10.0: PCI bridge to [bus 04-04]
[    0.327504] pci 0000:00:10.0:   bridge window [io  0x9000-0x9fff]
[    0.327508] pci 0000:00:10.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.327512] pci 0000:00:10.0:   bridge window [mem 0xfdb00000-0xfdbfffff pref]
[    0.327523] pci 0000:00:02.0: setting latency timer to 64
[    0.327529] pci 0000:00:03.0: setting latency timer to 64
[    0.327534] pci 0000:00:04.0: setting latency timer to 64
[    0.327538] pci 0000:00:10.0: setting latency timer to 64
[    0.327542] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.327545] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.327548] pci_bus 0000:00: resource 6 [mem 0x40000000-0xf3ffffff]
[    0.327550] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xffffffff]
[    0.327553] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.327555] pci_bus 0000:01: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.327558] pci_bus 0000:01: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.327561] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
[    0.327563] pci_bus 0000:02: resource 1 [mem 0xfd800000-0xfd8fffff]
[    0.327566] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.327568] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.327571] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.327574] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.327576] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.327579] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.327581] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff pref]
[    0.327584] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.327586] pci_bus 0000:04: resource 5 [mem 0x000a0000-0x000bffff]
[    0.327589] pci_bus 0000:04: resource 6 [mem 0x40000000-0xf3ffffff]
[    0.327592] pci_bus 0000:04: resource 7 [mem 0xf4000000-0xffffffff]
[    0.327634] NET: Registered protocol family 2
[    0.327702] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.327995] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.327995] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.327995] TCP: Hash tables configured (established 131072 bind 65536)
[    0.327995] TCP reno registered
[    0.327995] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.327995] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.327995] NET: Registered protocol family 1
[    0.327995] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.327995] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.327995] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.345085] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.345093] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.345146] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.345154] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    0.345209] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.345215] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.345272] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.345281] pci 0000:00:10.1: Enabling HT MSI Mapping
[    0.345293] pci 0000:03:00.0: Boot video device
[    0.345301] PCI: CLS 64 bytes, default 64
[    0.345331] Simple Boot Flag at 0x3a set to 0x1
[    0.345547] cpufreq-nforce2: No nForce2 chipset.
[    0.345578] Scanning for low memory corruption every 60 seconds
[    0.345736] audit: initializing netlink socket (disabled)
[    0.345747] type=2000 audit(1292844899.344:1): initialized
[    0.356136] highmem bounce pool size: 64 pages
[    0.356142] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.357552] VFS: Disk quotas dquot_6.5.2
[    0.357610] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.358203] fuse init (API version 7.14)
[    0.358284] msgmni has been set to 1709
[    0.358589] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.358593] io scheduler noop registered
[    0.358595] io scheduler deadline registered
[    0.358607] io scheduler cfq registered (default)
[    0.358743] pcieport 0000:00:02.0: setting latency timer to 64
[    0.358764]   alloc irq_desc for 40 on node -1
[    0.358766]   alloc kstat_irqs on node -1
[    0.358777] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.358829] pcieport 0000:00:03.0: setting latency timer to 64
[    0.358844]   alloc irq_desc for 41 on node -1
[    0.358845]   alloc kstat_irqs on node -1
[    0.358850] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.358895] pcieport 0000:00:04.0: setting latency timer to 64
[    0.358909]   alloc irq_desc for 42 on node -1
[    0.358911]   alloc kstat_irqs on node -1
[    0.358916] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.358986] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.359013] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.359225] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.359232] ACPI: Power Button [PWRB]
[    0.359296] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.359300] ACPI: Power Button [PWRF]
[    0.359726] ACPI: acpi_idle registered with cpuidle
[    0.363078] ERST: Table is not found!
[    0.363255] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.364620] brd: module loaded
[    0.365148] loop: module loaded
[    0.365741] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.365747]   alloc irq_desc for 23 on node -1
[    0.365749]   alloc kstat_irqs on node -1
[    0.365763] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.365810] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.365824] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.366115] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.366118]   alloc irq_desc for 22 on node -1
[    0.366120]   alloc kstat_irqs on node -1
[    0.366128] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.366144] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.366152] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.366489] Fixed MDIO Bus: probed
[    0.366527] PPP generic driver version 2.4.2
[    0.366570] tun: Universal TUN/TAP device driver, 1.6
[    0.366572] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.366651] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.366949] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.366952]   alloc irq_desc for 21 on node -1
[    0.366953]   alloc kstat_irqs on node -1
[    0.366962] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.366982] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.366985] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.367021] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.367048] ehci_hcd 0000:00:0b.1: debug port 1
[    0.367057] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.367083] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    0.367150] isapnp: Scanning for PnP cards...
[    0.416036] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.416173] hub 1-0:1.0: USB hub found
[    0.416178] hub 1-0:1.0: 8 ports detected
[    0.416263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.416573] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.416576]   alloc irq_desc for 20 on node -1
[    0.416577]   alloc kstat_irqs on node -1
[    0.416586] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.416595] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.416597] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.416630] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.416659] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
[    3.791961] Freeing initrd memory: 10504k freed
[    3.792038] hub 2-0:1.0: USB hub found
[    3.792045] hub 2-0:1.0: 8 ports detected
[    3.792128] uhci_hcd: USB Universal Host Controller Interface driver
[    3.792238] PNP: No PS/2 controller found. Probing ports directly.
[    3.800367] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.800379] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.800524] mice: PS/2 mouse device common for all mice
[    3.800657] rtc_cmos 00:04: RTC can wake from S4
[    3.800708] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.800743] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.800869] device-mapper: uevent: version 1.0.3
[    3.801056] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    3.801130] device-mapper: multipath: version 1.1.1 loaded
[    3.801133] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.801263] EISA: Probing bus 0 at eisa.0
[    3.801267] EISA: Cannot allocate resource for mainboard
[    3.801270] Cannot allocate resource for EISA slot 1
[    3.801272] Cannot allocate resource for EISA slot 2
[    3.801275] Cannot allocate resource for EISA slot 3
[    3.801277] Cannot allocate resource for EISA slot 4
[    3.801279] Cannot allocate resource for EISA slot 5
[    3.801281] Cannot allocate resource for EISA slot 6
[    3.801284] Cannot allocate resource for EISA slot 7
[    3.801286] Cannot allocate resource for EISA slot 8
[    3.801288] EISA: Detected 0 cards.
[    3.801367] cpuidle: using governor ladder
[    3.801369] cpuidle: using governor menu
[    3.801680] TCP cubic registered
[    3.801801] NET: Registered protocol family 10
[    3.802181] lo: Disabled Privacy Extensions
[    3.802394] NET: Registered protocol family 17
[    3.802436] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 cpu cores) (version 2.20.00)
[    3.802501] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
[    3.802503] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc
[    3.802506] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe
[    3.802508] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    3.802556] Using IPI No-Shortcut mode
[    3.802648] PM: Resume from disk failed.
[    3.802663] registered taskstats version 1
[    3.802902]   Magic number: 6:734:580
[    3.802955] pci_bus 0000:01: hash matches
[    3.802965] pci_link PNP0C0F:23: hash matches
[    3.803031] rtc_cmos 00:04: setting system clock to 2010-12-20 11:36:05 UTC (1292844965)
[    3.803034] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.803036] EDD information not available.
[    4.005019] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.054490] isapnp: No Plug & Play device found
[    4.054517] Freeing unused kernel memory: 684k freed
[    4.055032] Write protecting the kernel text: 4932k
[    4.055072] Write protecting the kernel read-only data: 1976k
[    4.074516] udev[75]: starting version 163
[    4.183121] sata_nv 0000:00:0e.0: version 3.5
[    4.183156] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    4.183160] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.183250] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.212135] scsi0 : sata_nv
[    4.231926] scsi1 : sata_nv
[    4.232171] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    4.232175] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    4.232223] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    4.232226] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    4.232288] sata_nv 0000:00:0f.0: setting latency timer to 64
[    4.237807] scsi2 : sata_nv
[    4.237920] scsi3 : sata_nv
[    4.238135] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
[    4.238139] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
[    4.244533] Initializing USB Mass Storage driver...
[    4.244722] scsi4 : usb-storage 1-1:1.0
[    4.244836] usbcore: registered new interface driver usb-storage
[    4.244839] USB Mass Storage support registered.
[    4.372027] usb 2-5: new low speed USB device using ohci_hcd and address 2
[    4.700046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.705030] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.709317] ata1.00: ATA-7: WDC WD2500JS-75NCB3, 10.02E04, max UDMA/133
[    4.709321] ata1.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.724323] ata1.00: configured for UDMA/133
[    4.724541] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-75N 10.0 PQ: 0 ANSI: 5
[    4.724750] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.724846] sd 0:0:0:0: [sda] 488281250 512-byte logical blocks: (250 GB/232 GiB)
[    4.724896] sd 0:0:0:0: [sda] Write Protect is off
[    4.724899] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.724920] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.725097]  sda:
[    4.741196] ata3.00: ATAPI: TSSTcorp DVD+/-RW TS-H553A, DE04, max UDMA/33
[    4.741208] ata3.00: applying bridge limits
[    4.749024]  sda1 sda2 <
[    4.764030] usb 2-6: new low speed USB device using ohci_hcd and address 3
[    4.781969]  sda5 >
[    4.782248] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.797217] ata3.00: configured for UDMA/33
[    4.988229] usbcore: registered new interface driver hiddev
[    4.994506] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input2
[    4.994604] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:0b.0-5/input0
[    5.001423] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input3
[    5.001505] generic-usb 0003:413C:3200.0002: input,hidraw1: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:0b.0-6/input0
[    5.001523] usbcore: registered new interface driver usbhid
[    5.001525] usbhid: USB HID core driver
[    5.036035] ata2: SATA link down (SStatus 0 SControl 300)
[    5.037411] scsi 2:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H553A DE04 PQ: 0 ANSI: 5
[    5.047536] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.047540] Uniform CD-ROM driver Revision: 3.20
[    5.047654] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    5.047715] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    5.254372] scsi 4:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.08 PQ: 0 ANSI: 0
[    5.258104] scsi 4:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.08 PQ: 0 ANSI: 0
[    5.261727] scsi 4:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.08 PQ: 0 ANSI: 0
[    5.264853] scsi 4:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.08 PQ: 0 ANSI: 0
[    5.265449] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    5.265709] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    5.265866] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    5.266027] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    5.281844] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    5.286468] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    5.290599] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    5.298470] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    5.356031] ata4: SATA link down (SStatus 0 SControl 300)
[    5.359564] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    5.359572]   alloc irq_desc for 19 on node -1
[    5.359575]   alloc kstat_irqs on node -1
[    5.359588] b44 0000:04:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    5.359598] b44 0000:04:07.0: setting latency timer to 64
[    5.380091] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    5.380100] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    5.380106] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    5.424090] ssb: Sonics Silicon Backplane found on PCI device 0000:04:07.0
[    5.424119] b44: b44.c:v2.0
[    5.444793] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:18:8b:73:58:86
[    5.652328] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.652334] EXT4-fs (sda1): write access will be enabled during recovery
[    7.258115] EXT4-fs (sda1): recovery complete
[    7.258494] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.313812] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
[   18.441988] udev[516]: starting version 163
[   18.461109] lp: driver loaded but no devices found
[   18.613800] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.731549] type=1400 audit(1292844980.423:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=818 comm="apparmor_parser"
[   18.731851] type=1400 audit(1292844980.423:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=818 comm="apparmor_parser"
[   18.732017] type=1400 audit(1292844980.423:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=818 comm="apparmor_parser"
[   18.794539] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.816181] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   21.816188] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   21.816444] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.538420] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   28.538467] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   28.540768] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   28.551608] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   28.690582] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   28.690592] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   28.690597] hda_intel: Disable MSI for Nvidia chipset
[   28.690641] HDA Intel 0000:00:10.1: setting latency timer to 64
[   28.696956] type=1400 audit(1292844990.389:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1012 comm="apparmor_parser"
[   28.697441] type=1400 audit(1292844990.389:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1013 comm="apparmor_parser"
[   28.697788] type=1400 audit(1292844990.389:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1013 comm="apparmor_parser"
[   28.697961] type=1400 audit(1292844990.389:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1013 comm="apparmor_parser"
[   28.703243] type=1400 audit(1292844990.393:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1016 comm="apparmor_parser"
[   28.703739] type=1400 audit(1292844990.393:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1016 comm="apparmor_parser"
[   28.706724] type=1400 audit(1292844990.397:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1017 comm="apparmor_parser"
[   28.707758] type=1400 audit(1292844990.397:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1014 comm="apparmor_parser"
[   28.711859] type=1400 audit(1292844990.401:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1014 comm="apparmor_parser"
[   28.714481] type=1400 audit(1292844990.405:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1014 comm="apparmor_parser"
[   29.450755] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   29.740215] input: HDA NVidia Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input4
[   29.740332] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input5
[   29.740396] input: HDA NVidia Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input6
[   29.740458] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
[   29.740517] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
[   29.740579] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input9
[   29.740637] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input10
[   29.740701] input: HDA NVidia HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input11
[   32.400021] eth0: no IPv6 routers present
[   38.540164] Linux agpgart interface v0.103
[   38.572033] [drm] Initialized drm 1.1.0 20060810
[   38.616545] [drm] radeon defaulting to kernel modesetting.
[   38.616549] [drm] radeon kernel modesetting enabled.
[   38.616995] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   38.617021]   alloc irq_desc for 16 on node -1
[   38.617027]   alloc kstat_irqs on node -1
[   38.617042] radeon 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   38.617052] radeon 0000:03:00.0: setting latency timer to 64
[   38.619047] [drm] initializing kernel modesetting (RV515 0x1002:0x7183).
[   38.619211] [drm] register mmio base: 0xFDDF0000
[   38.619214] [drm] register mmio size: 65536
[   38.619975] ATOM BIOS: 113
[   38.620020] [drm] Generation 2 PCI interface, using max accessible memory
[   38.620025] radeon 0000:03:00.0: VRAM: 256M 0x00000000 - 0x0FFFFFFF (256M used)
[   38.620030] radeon 0000:03:00.0: GTT: 512M 0x10000000 - 0x2FFFFFFF
[   38.620100]   alloc irq_desc for 43 on node -1
[   38.620103]   alloc kstat_irqs on node -1
[   38.620113] radeon 0000:03:00.0: irq 43 for MSI/MSI-X
[   38.620118] radeon 0000:03:00.0: radeon: using MSI.
[   38.620141] [drm] radeon: irq initialized.
[   38.620382] [drm] Detected VRAM RAM=256M, BAR=256M
[   38.620388] [drm] RAM width 128bits DDR
[   38.620527] [TTM] Zone  kernel: Available graphics memory: 443214 kiB.
[   38.620532] [TTM] Zone highmem: Available graphics memory: 512274 kiB.
[   38.620535] [TTM] Initializing pool allocator.
[   38.620561] [drm] radeon: 256M of VRAM memory ready
[   38.620563] [drm] radeon: 512M of GTT memory ready.
[   38.620590] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   38.623688] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   38.625172] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   38.625258] [drm] Loading R500 Microcode
[   48.645748] [drm] radeon: ring at 0x0000000010000000
[   48.645781] [drm] ring test succeeded in 8 usecs
[   48.645937] [drm] radeon: ib pool ready.
[   48.646408] [drm] ib test succeeded in 0 usecs
[   48.646417] failed to evaluate ATIF got AE_BAD_PARAMETER
[   48.646421] radeon 0000:03:00.0: Error during ACPI methods call
[   48.646500] [drm] Default TV standard: NTSC
[   48.646502] [drm] Default TV standard: NTSC
[   48.646598] [drm] Default TV standard: NTSC
[   48.646677] [drm] Radeon Display Connectors
[   48.646680] [drm] Connector 0:
[   48.646681] [drm]   DVI-I
[   48.646683] [drm]   HPD1
[   48.646686] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   48.646688] [drm]   Encoders:
[   48.646690] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   48.646692] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   48.646694] [drm] Connector 1:
[   48.646695] [drm]   S-video
[   48.646697] [drm]   Encoders:
[   48.646698] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   48.646700] [drm] Connector 2:
[   48.646701] [drm]   VGA
[   48.646704] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   48.646706] [drm]   Encoders:
[   48.646707] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   48.789531] [drm] fb mappable at 0xD00C0000
[   48.789533] [drm] vram apper at 0xD0000000
[   48.789536] [drm] size 5242880
[   48.789537] [drm] fb depth is 24
[   48.789539] [drm]    pitch is 5120
[   48.820246] Console: switching to colour frame buffer device 160x64
[   48.826501] fb0: radeondrmfb frame buffer device
[   48.826503] drm: registered panic notifier
[   48.826506] Slow work thread pool: Starting up
[   48.826646] Slow work thread pool: Ready
[   48.826653] [drm] Initialized radeon 2.5.0 20080528 for 0000:03:00.0 on minor 0
[   60.525667] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   90.169026] Clocksource tsc unstable (delta = -218769561 ns)
[   98.904854] ppdev: user-space parallel port driver

```So here I am. If someone has an idea of how solve this problem. Either a new solution or by telling me how to upgrade my bios or add this kernel line, I will be very thankfull

---

