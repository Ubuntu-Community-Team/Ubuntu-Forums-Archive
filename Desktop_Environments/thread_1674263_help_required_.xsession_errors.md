---
title: "help required: .xsession_errors"
date: 2011-01-23
forum: Desktop Environments
---

### Post by f.pelosa on 2011-01-23
hello,
every time I boot 10.04 on my laptop, the file ~/.xsession-errors is created. Could you please help me figuring out what's wrong? 
Thanks a lot!
Ale

I post here the content of my ~/.xsession-errors and the output of dmesg:
NB: I'm running 10.04 on a Dell laptop m101z.

~/.xsession-errors:

/etc/gdm/Xsession: Beginning session setup...
/home/ale/Downloads was removed, reassigning DOWNLOAD to homedir
/home/ale/Templates was removed, reassigning TEMPLATES to homedir
/home/ale/Documents was removed, reassigning DOCUMENTS to homedir
/home/ale/Music was removed, reassigning MUSIC to homedir
/home/ale/Pictures was removed, reassigning PICTURES to homedir
/home/ale/Videos was removed, reassigning VIDEOS to homedir
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-NOUzDE
GNOME_KEYRING_CONTROL=/tmp/keyring-NOUzDE
GNOME_KEYRING_CONTROL=/tmp/keyring-NOUzDE
SSH_AUTH_SOCK=/tmp/keyring-NOUzDE/ssh
Window manager warning: Failed to read saved session file /home/ale/.config/metacity/sessions/10fd708a5fa185c1bb129581511622092800000013280029.ms: Failed to open file '/home/ale/.config/metacity/sessions/10fd708a5fa185c1bb129581511622092800000013280029.ms': No such file or directory

(gnome-power-manager:1394): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x96c6c0'
** (nm-applet:1395): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1395): DEBUG: old state indicates that this was not a disconnect 0

(polkit-gnome-authentication-agent-1:1398): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1398): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1395): DEBUG: foo_client_state_changed_cb
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** (nm-applet:1395): DEBUG: going for offline with icon: notification-network-disconnected
Initializing nautilus-gdu extension
** (nm-applet:1395): DEBUG: going for offline with icon: notification-network-disconnected

** (gnome-screensaver:1470): WARNING **: screensaver already running in this session
** Message: RFKILL event: idx 0 type 2 op 1 soft 0 hard 0

** Message: removing killswitch idx 0
** Message: RFKILL event: idx 1 type 2 op 0 soft 0 hard 0

** Message: adding killswitch idx 1 state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: RFKILL event: idx 1 type 2 op 2 soft 0 hard 0

** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: RFKILL event: idx 1 type 2 op 2 soft 1 hard 0

** Message: updating killswitch status 1
** Message: killswitch 1 is 0
** Message: killswitches state 0
** Message: killswitch 1 is 0
** Message: killswitches state 0
evolution-alarm-notify-Message: Setting timeout for 12053 1295827200 1295815147
evolution-alarm-notify-Message:  Mon Jan 24 01:00:00 2011

evolution-alarm-notify-Message:  Sun Jan 23 21:39:07 2011

** (nm-applet:1395): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1395): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1395): DEBUG: foo_client_state_changed_cb
** (nm-applet:1395): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:1395): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:1395): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:1395): DEBUG: foo_client_state_changed_cb
** (nm-applet:1395): DEBUG: foo_client_state_changed_cb
** (update-notifier:1575): DEBUG: Skipping reboot required

(gnome-display-properties:4048): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:4048): Gtk-WARNING **: No object called: 
** (gnome-screensaver-preferences:4052): DEBUG: Found best visual for GL: 0x27


dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-27-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 (Ubuntu 2.6.32-27.49-generic 2.6.32.26+drm33.12)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=3c8b60dd-9665-4b41-bc82-fba52cf6d36f ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afe8e000 (usable)
[    0.000000]  BIOS-e820: 00000000afe8e000 - 00000000afea0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afea0000 - 00000000afeb0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeb0000 - 00000000afeb3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afeb3000 - 00000000afeff000 (reserved)
[    0.000000]  BIOS-e820: 00000000aff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xafe8e max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000afe8e000 (usable)
[    0.000000]  modified: 00000000afe8e000 - 00000000afea0000 (ACPI NVS)
[    0.000000]  modified: 00000000afea0000 - 00000000afeb0000 (ACPI data)
[    0.000000]  modified: 00000000afeb0000 - 00000000afeb3000 (ACPI NVS)
[    0.000000]  modified: 00000000afeb3000 - 00000000afeff000 (reserved)
[    0.000000]  modified: 00000000aff00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000afe8e000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afe8e000 page 4k
[    0.000000] kernel direct mapping tables up to afe8e000 @ 8000-b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 1G
[    0.000000] kernel direct mapping tables up to 140000000 @ a000-b000
[    0.000000] RAMDISK: 377fc000 - 37fef85b
[    0.000000] ACPI: RSDP 00000000000f7a80 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000afea1959 0008C (v01 DELL    CL09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000afeaf013 000F4 (v03 DELL   CL09     06040000 AMD  000F4240)
[    0.000000] ACPI: DSDT 00000000afea19e5 0D62E (v01   DELL     CL09 06040000 MSFT 04000000)
[    0.000000] ACPI: FACS 00000000afeb2fc0 00040
[    0.000000] ACPI: TCPA 00000000afeaf17b 00032 (v02 DELL   CL09     06040000 PTEC 00000000)
[    0.000000] ACPI: EINJ 00000000afeaf1ad 001B0 (v01 PTL    WHEAPTL  06040000 PTL  00000001)
[    0.000000] ACPI: HEST 00000000afeaf35d 002E4 (v01 PTL    WHEAPTL  06040000 PTL  00000001)
[    0.000000] ACPI: BERT 00000000afeaf641 00030 (v01 PTL    WHEAPTL  06040000 PTL  00000001)
[    0.000000] ACPI: SSDT 00000000afeaf671 000E1 (v01 wheaos  wheaosc 06040000 INTL 20050624)
[    0.000000] ACPI: ERST 00000000afeaf752 00270 (v01 PTL    WHEAPTL  06040000 PTL  00000001)
[    0.000000] ACPI: OSFR 00000000afeaf9c2 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: APIC 00000000afeafa32 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000afeafa90 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000afeafacc 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000afeafb04 00176 (v01 DELL    CL09    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000afeafc7a 00386 (v01 AMD    POWERNOW 06040000 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  0000000000036fff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fa64]    TEXT DATA BSS ==> [0001000000 - 0001a2fa64]
[    0.000000]   #3 [00377fc000 - 0037fef85b]          RAMDISK ==> [00377fc000 - 0037fef85b]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a30170]              BRK ==> [0001a30000 - 0001a30170]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f7ab0] f7ab0
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000afe8e
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982566
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702150 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afe8e000 - 00000000afea0000
[    0.000000] PM: Registered nosave memory: 00000000afea0000 - 00000000afeb0000
[    0.000000] PM: Registered nosave memory: 00000000afeb0000 - 00000000afeb3000
[    0.000000] PM: Registered nosave memory: 00000000afeb3000 - 00000000afeff000
[    0.000000] PM: Registered nosave memory: 00000000afeff000 - 00000000aff00000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 964543
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=3c8b60dd-9665-4b41-bc82-fba52cf6d36f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 29c8000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3790360k/5242880k available (5422k kernel code, 1312616k absent, 139904k reserved, 2979k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1396.385 MHz processor.
[    0.020007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2792.76 BogoMIPS (lpj=13963830)
[    0.020037] Security Framework initialized
[    0.020062] AppArmor: AppArmor initialized
[    0.020566] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.022542] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.023421] Mount-cache hash table entries: 256
[    0.023585] Initializing cgroup subsys ns
[    0.023590] Initializing cgroup subsys cpuacct
[    0.023596] Initializing cgroup subsys memory
[    0.023605] Initializing cgroup subsys devices
[    0.023609] Initializing cgroup subsys freezer
[    0.023612] Initializing cgroup subsys net_cls
[    0.023635] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.023638] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.023642] CPU 0/0x0 -> Node 0
[    0.023646] tseg: 00aff00000
[    0.023649] CPU: Physical Processor ID: 0
[    0.023651] CPU: Processor Core ID: 0
[    0.023655] mce: CPU supports 6 MCE banks
[    0.023668] using C1E aware idle routine
[    0.023671] Performance Events: AMD PMU driver.
[    0.023678] ... version:                0
[    0.023680] ... bit width:              48
[    0.023683] ... generic registers:      4
[    0.023685] ... value mask:             0000ffffffffffff
[    0.023688] ... max period:             00007fffffffffff
[    0.023691] ... fixed-purpose events:   0
[    0.023693] ... event mask:             000000000000000f
[    0.026047] ACPI: Core revision 20090903
[    0.060010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060018] ftrace: allocating 22535 entries in 89 pages
[    0.070113] Setting APIC routing to flat
[    0.070429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.171005] CPU0: AMD Athlon(tm) II Neo K345 Dual-Core Processor stepping 03
[    0.180000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.330102] CPU1: AMD Athlon(tm) II Neo K345 Dual-Core Processor stepping 03
[    0.330116] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.340019] Brought up 2 CPUs
[    0.340022] Total of 2 processors activated (5585.82 BogoMIPS).
[    0.340028] System has AMD C1E enabled
[    0.340041] Switch to broadcast mode on CPU1
[    0.340306] CPU0 attaching sched-domain:
[    0.340310]  domain 0: span 0-1 level MC
[    0.340313]   groups: 0 1
[    0.340320] CPU1 attaching sched-domain:
[    0.340323]  domain 0: span 0-1 level MC
[    0.340326]   groups: 1 0
[    0.340416] Switch to broadcast mode on CPU0
[    0.340416] devtmpfs: initialized
[    0.340416] regulator: core version 0.5
[    0.340416] Time: 21:38:09  Date: 01/23/11
[    0.340416] NET: Registered protocol family 16
[    0.340416] Trying to unpack rootfs image as initramfs...
[    0.340416] node 0 link 0: io port [1000, ffff]
[    0.340416] TOM: 00000000c0000000 aka 3072M
[    0.340416] Fam 10h mmconf [e0000000, efffffff]
[    0.340416] node 0 link 0: mmio [c0000000, d01fffff]
[    0.340416] node 0 link 0: mmio [d0200000, dfffffff]
[    0.340416] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.340416] node 0 link 0: mmio [f0000000, ffdfffff]
[    0.340416] TOM2: 0000000140000000 aka 5120M
[    0.340416] bus: [00,1f] on node 0 link 0
[    0.340416] bus: 00 index 0 io port: [0, ffff]
[    0.340416] bus: 00 index 1 mmio: [c0000000, dfffffff]
[    0.340416] bus: 00 index 2 mmio: [f0000000, ffffffff]
[    0.340416] bus: 00 index 3 mmio: [140000000, fcffffffff]
[    0.340416] ACPI: bus type pci registered
[    0.340489] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 3
[    0.340492] PCI: Not using MMCONFIG.
[    0.340495] PCI: Using configuration type 1 for base access
[    0.340497] PCI: Using configuration type 1 for extended access
[    0.340532] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.340534] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.340536] mtrr: probably your BIOS does not setup all CPUs.
[    0.340538] mtrr: corrected configuration.
[    0.350229] bio: create slab <bio-0> at 0
[    0.351517] ACPI: EC: Look up EC in DSDT
[    0.353508] ACPI Warning for \_SB_._OSC: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    0.353518] \_SB_:_OSC evaluation returned wrong type
[    0.353521] _OSC request data:1 7 
[    0.358370] ACPI: BIOS _OSI(Linux) query ignored
[    0.430087] ACPI: Interpreter enabled
[    0.430094] ACPI: (supports S0 S3 S4 S5)
[    0.430127] ACPI: Using IOAPIC for interrupt routing
[    0.430601] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 3
[    0.490242] PCI: BIOS Bug: MCFG area at e0000000 is not reserved in ACPI motherboard resources
[    0.490247] PCI: Not using MMCONFIG.
[    0.490676] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.490885] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.550784] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.551146] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.551940] ACPI: No dock devices found.
[    0.553869] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.554062] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.554066] pci 0000:00:04.0: PME# disabled
[    0.554118] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.554122] pci 0000:00:05.0: PME# disabled
[    0.554198] pci 0000:00:11.0: reg 10 io port: [0x8440-0x8447]
[    0.554207] pci 0000:00:11.0: reg 14 io port: [0x8430-0x8433]
[    0.554216] pci 0000:00:11.0: reg 18 io port: [0x8420-0x8427]
[    0.554224] pci 0000:00:11.0: reg 1c io port: [0x8410-0x8413]
[    0.554232] pci 0000:00:11.0: reg 20 io port: [0x8400-0x840f]
[    0.554241] pci 0000:00:11.0: reg 24 32bit mmio: [0xd0606800-0xd0606bff]
[    0.554313] pci 0000:00:12.0: reg 10 32bit mmio: [0xd0404000-0xd0404fff]
[    0.554394] pci 0000:00:12.2: reg 10 32bit mmio: [0xd0606000-0xd06060ff]
[    0.554451] pci 0000:00:12.2: supports D1 D2
[    0.554454] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.554460] pci 0000:00:12.2: PME# disabled
[    0.554495] pci 0000:00:13.0: reg 10 32bit mmio: [0xd0405000-0xd0405fff]
[    0.554579] pci 0000:00:13.2: reg 10 32bit mmio: [0xd0606400-0xd06064ff]
[    0.554636] pci 0000:00:13.2: supports D1 D2
[    0.554639] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.554644] pci 0000:00:13.2: PME# disabled
[    0.554753] pci 0000:00:14.2: reg 10 64bit mmio: [0xd0400000-0xd0403fff]
[    0.554801] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.554806] pci 0000:00:14.2: PME# disabled
[    0.555057] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.555063] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.555068] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.555079] pci 0000:01:05.0: reg 24 32bit mmio: [0xd0000000-0xd00fffff]
[    0.555096] pci 0000:01:05.0: supports D1 D2
[    0.555123] pci 0000:01:05.1: reg 10 32bit mmio: [0xd0110000-0xd0113fff]
[    0.555152] pci 0000:01:05.1: supports D1 D2
[    0.555203] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.555208] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd01fffff]
[    0.555214] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.555268] pci 0000:02:00.0: reg 10 64bit mmio: [0xd0200000-0xd023ffff]
[    0.555278] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa07f]
[    0.555340] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.555346] pci 0000:02:00.0: PME# disabled
[    0.555416] pci 0000:00:04.0: bridge io port: [0xa000-0xafff]
[    0.555420] pci 0000:00:04.0: bridge 32bit mmio: [0xd0200000-0xd02fffff]
[    0.555511] pci 0000:03:00.0: reg 10 64bit mmio: [0xd0300000-0xd0303fff]
[    0.555577] pci 0000:03:00.0: supports D1 D2
[    0.555580] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.555587] pci 0000:03:00.0: PME# disabled
[    0.555694] pci 0000:00:05.0: bridge 32bit mmio: [0xd0300000-0xd03fffff]
[    0.555759] pci 0000:00:14.4: transparent bridge
[    0.555786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.556114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.556221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.556383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.556528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.562657] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0
[    0.562899] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0
[    0.563157] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0
[    0.563413] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0
[    0.563643] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0
[    0.563825] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0
[    0.564002] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0
[    0.564178] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0
[    0.564337] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.564343] vgaarb: loaded
[    0.564479] SCSI subsystem initialized
[    0.564581] libata version 3.00 loaded.
[    0.564672] usbcore: registered new interface driver usbfs
[    0.564687] usbcore: registered new interface driver hub
[    0.564720] usbcore: registered new device driver usb
[    0.564893] ACPI: WMI: Mapper loaded
[    0.564896] PCI: Using ACPI for IRQ routing
[    0.565117] NetLabel: Initializing
[    0.565120] NetLabel:  domain hash size = 128
[    0.565122] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.565139] NetLabel:  unlabeled traffic allowed by default
[    0.565214] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.565220] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.567261] Switching to clocksource tsc
[    0.567702] AppArmor: AppArmor Filesystem Enabled
[    0.567702] pnp: PnP ACPI init
[    0.567702] ACPI: bus type pnp registered
[    0.592581] pnp: PnP ACPI: found 10 devices
[    0.592586] ACPI: ACPI bus type pnp unregistered
[    0.592612] system 00:01: ioport range 0xf50-0xf51 has been reserved
[    0.592619] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.592624] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.592637] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.592641] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.592645] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.592649] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.592653] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.592657] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.592660] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.592664] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.592668] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.592672] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.592676] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.592680] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.592684] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.592688] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.592692] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.592696] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.592700] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.592704] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.592713] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.592717] system 00:09: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.592722] system 00:09: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.592726] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.592730] system 00:09: iomem range 0xfed61000-0xfed613ff has been reserved
[    0.592734] system 00:09: iomem range 0xfed80000-0xfed80fff has been reserved
[    0.594779] Freeing initrd memory: 8142k freed
[    0.597708] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.597713] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.597718] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd01fffff
[    0.597723] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.597730] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.597734] pci 0000:00:04.0:   IO window: 0xa000-0xafff
[    0.597739] pci 0000:00:04.0:   MEM window: 0xd0200000-0xd02fffff
[    0.597743] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.597749] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    0.597752] pci 0000:00:05.0:   IO window: disabled
[    0.597757] pci 0000:00:05.0:   MEM window: 0xd0300000-0xd03fffff
[    0.597761] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.597767] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.597770] pci 0000:00:14.4:   IO window: disabled
[    0.597776] pci 0000:00:14.4:   MEM window: disabled
[    0.597781] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.597811]   alloc irq_desc for 16 on node 0
[    0.597814]   alloc kstat_irqs on node 0
[    0.597825] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.597830] pci 0000:00:04.0: setting latency timer to 64
[    0.597838]   alloc irq_desc for 17 on node 0
[    0.597841]   alloc kstat_irqs on node 0
[    0.597846] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.597851] pci 0000:00:05.0: setting latency timer to 64
[    0.597862] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.597866] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.597870] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.597874] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd01fffff]
[    0.597878] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.597882] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.597886] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xd02fffff]
[    0.597890] pci_bus 0000:03: resource 1 mem: [0xd0300000-0xd03fffff]
[    0.597893] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.597897] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.597956] NET: Registered protocol family 2
[    0.598203] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.599851] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.603743] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.604222] TCP: Hash tables configured (established 524288 bind 65536)
[    0.604225] TCP reno registered
[    0.604344] NET: Registered protocol family 1
[    0.642507] pci 0000:01:05.0: Boot video device
[    0.643720] PCI-DMA: Disabling AGP.
[    0.643878] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.643881] PCI-DMA: using GART IOMMU.
[    0.643887] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.645775] Scanning for low memory corruption every 60 seconds
[    0.645951] audit: initializing netlink socket (disabled)
[    0.645975] type=2000 audit(1295818688.642:1): initialized
[    0.658984] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.660924] VFS: Disk quotas dquot_6.5.2
[    0.661007] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.661898] fuse init (API version 7.13)
[    0.662057] msgmni has been set to 7418
[    0.662475] alg: No test for stdrng (krng)
[    0.662598] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.662603] io scheduler noop registered
[    0.662606] io scheduler anticipatory registered
[    0.662608] io scheduler deadline registered
[    0.662658] io scheduler cfq registered (default)
[    0.662991]   alloc irq_desc for 24 on node 0
[    0.662996]   alloc kstat_irqs on node 0
[    0.663007] pcieport 0000:00:04.0: irq 24 for MSI/MSI-X
[    0.663015] pcieport 0000:00:04.0: setting latency timer to 64
[    0.663248]   alloc irq_desc for 25 on node 0
[    0.663251]   alloc kstat_irqs on node 0
[    0.663259] pcieport 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.663266] pcieport 0000:00:05.0: setting latency timer to 64
[    0.663417] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.663452] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.682552] ACPI: AC Adapter [ACAD] (off-line)
[    0.682661] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.682666] ACPI: Power Button [PWRB]
[    0.682739] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.682870] ACPI: Lid Switch [LID]
[    0.682920] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.682924] ACPI: Power Button [PWRF]
[    0.683235] ACPI: processor limited to max C-state 1
[    0.683278] processor LNXCPU:00: registered as cooling_device0
[    0.683327] processor LNXCPU:01: registered as cooling_device1
[    0.734391] Linux agpgart interface v0.103
[    0.734434] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.735834] brd: module loaded
[    0.736374] loop: module loaded
[    0.736472] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.736938] Fixed MDIO Bus: probed
[    0.736977] PPP generic driver version 2.4.2
[    0.737021] tun: Universal TUN/TAP device driver, 1.6
[    0.737024] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.737109] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.737232] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.737276] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.737400] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.737461] ehci_hcd 0000:00:12.2: debug port 1
[    0.737494] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd0606000
[    0.752435] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.752589] usb usb1: configuration #1 chosen from 1 choice
[    0.752626] hub 1-0:1.0: USB hub found
[    0.752637] hub 1-0:1.0: 5 ports detected
[    0.752811] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.752841] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.752892] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.752937] ehci_hcd 0000:00:13.2: debug port 1
[    0.752957] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0606400
[    0.772513] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.772664] usb usb2: configuration #1 chosen from 1 choice
[    0.772698] hub 2-0:1.0: USB hub found
[    0.772710] hub 2-0:1.0: 5 ports detected
[    0.772836] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.772976]   alloc irq_desc for 18 on node 0
[    0.772980]   alloc kstat_irqs on node 0
[    0.772989] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.773022] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.773094] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.773136] ohci_hcd 0000:00:12.0: irq 18, io mem 0xd0404000
[    0.836614] usb usb3: configuration #1 chosen from 1 choice
[    0.836652] hub 3-0:1.0: USB hub found
[    0.836700] hub 3-0:1.0: 5 ports detected
[    0.836867] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.836896] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.836946] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    0.836977] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0405000
[    0.896607] usb usb4: configuration #1 chosen from 1 choice
[    0.896642] hub 4-0:1.0: USB hub found
[    0.896658] hub 4-0:1.0: 5 ports detected
[    0.896780] uhci_hcd: USB Universal Host Controller Interface driver
[    0.896891] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.911082] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.911089] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.911222] mice: PS/2 mouse device common for all mice
[    0.911357] rtc_cmos 00:04: RTC can wake from S4
[    0.911417] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.911451] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.911612] device-mapper: uevent: version 1.0.3
[    0.911901] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.912109] device-mapper: multipath: version 1.1.0 loaded
[    0.912115] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.912612] cpuidle: using governor ladder
[    0.912616] cpuidle: using governor menu
[    0.913094] TCP cubic registered
[    0.913281] NET: Registered protocol family 10
[    0.913855] lo: Disabled Privacy Extensions
[    0.914241] NET: Registered protocol family 17
[    0.914295] powernow-k8: Found 1 AMD Athlon(tm) II Neo K345 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    0.914349] powernow-k8:    0 : pstate 0 (1400 MHz)
[    0.914352] powernow-k8:    1 : pstate 1 (1200 MHz)
[    0.914354] powernow-k8:    2 : pstate 2 (800 MHz)
[    0.914673] PM: Resume from disk failed.
[    0.914689] registered taskstats version 1
[    0.915077]   Magic number: 11:506:652
[    0.915233] rtc_cmos 00:04: setting system clock to 2011-01-23 21:38:09 UTC (1295818689)
[    0.915237] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.915240] EDD information not available.
[    0.915316] Freeing unused kernel memory: 876k freed
[    0.915615] Write protecting the kernel read-only data: 7696k
[    0.923644] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.943882] udev: starting version 151
[    1.088751] ahci 0000:00:11.0: version 3.0
[    1.088805]   alloc irq_desc for 19 on node 0
[    1.088808]   alloc kstat_irqs on node 0
[    1.088818] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.088892]   alloc irq_desc for 26 on node 0
[    1.088895]   alloc kstat_irqs on node 0
[    1.088907] ahci 0000:00:11.0: irq 26 for MSI/MSI-X
[    1.088994] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x9 impl SATA mode
[    1.088999] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.093030] scsi0 : ahci
[    1.093213] scsi1 : ahci
[    1.093323] scsi2 : ahci
[    1.093410] scsi3 : ahci
[    1.093730] ata1: SATA max UDMA/133 abar m1024@0xd0606800 port 0xd0606900 irq 26
[    1.093734] ata2: DUMMY
[    1.093736] ata3: DUMMY
[    1.093740] ata4: SATA max UDMA/133 abar m1024@0xd0606800 port 0xd0606a80 irq 26
[    1.210136] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.440256] ata4: SATA link down (SStatus 0 SControl 300)
[    1.462805] ACPI: Battery Slot [BAT1] (battery present)
[    1.619113] usb 2-4: configuration #1 chosen from 1 choice
[    1.622583] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.624823] ata1.00: ATA-8: WDC WD3200BEKT-75PVMT0, 01.01A01, max UDMA/133
[    1.624828] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.627273] ata1.00: configured for UDMA/133
[    1.632868] Initializing USB Mass Storage driver...
[    1.633015] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.633128] usbcore: registered new interface driver usb-storage
[    1.633132] USB Mass Storage support registered.
[    1.633138] usb-storage: device found at 2
[    1.633141] usb-storage: waiting for device to settle before scanning
[    1.650359] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-7 01.0 PQ: 0 ANSI: 5
[    1.650607] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.650669] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.650812] sd 0:0:0:0: [sda] Write Protect is off
[    1.650816] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.650867] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.651565]  sda: sda1 < sda5 > sda2 sda3
[    1.711060] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.742611] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    2.007102] usb 2-5: configuration #1 chosen from 1 choice
[    2.071696] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.071704] EXT4-fs (sda5): write access will be enabled during recovery
[    2.332579] usb 3-5: new full speed USB device using ohci_hcd and address 2
[    2.528837] usb 3-5: configuration #1 chosen from 1 choice
[    3.195501] EXT4-fs (sda5): orphan cleanup on readonly fs
[    3.195513] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10748351
[    3.195598] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10748191
[    3.195618] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10748298
[    3.195656] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10748220
[    3.195672] EXT4-fs (sda5): 4 orphan inodes deleted
[    3.195676] EXT4-fs (sda5): recovery complete
[    4.108940] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.632957] usb-storage: device scan complete
[    6.635554] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.636305] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   11.546272] udev: starting version 151
[   11.549129] Adding 4096564k swap on /dev/sda2.  Priority:-1 extents:1 across:4096564k 
[   11.658505] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   11.700605] acpi device:34: registered as cooling_device2
[   11.700750] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:33/LNXVIDEO:02/input/input5
[   11.700821] ACPI: Video Device [VGA2] (multi-head: yes  rom: no  post: no)
[   11.854095] lib80211: common routines for IEEE802.11 drivers
[   11.854100] lib80211_crypt: registered algorithm 'NULL'
[   11.876074] atl1c 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.876091] atl1c 0000:02:00.0: setting latency timer to 64
[   11.887502] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.919457] ACPI: resource piix4_smbus [0x8040-0x8047] conflicts with ACPI region SMB0 [0x8040-0x804f]
[   11.919462] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.983211] Bluetooth: Core ver 2.15
[   11.987583] NET: Registered protocol family 31
[   11.987587] Bluetooth: HCI device and connection manager initialized
[   11.987592] Bluetooth: HCI socket layer initialized
[   11.990215] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.990569] usbcore: registered new interface driver btusb
[   12.010982] atl1c 0000:02:00.0: version 1.0.0.1-NAPI
[   12.011137] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.062847] type=1505 audit(1295815100.647:2):  operation="profile_load" pid=694 name="/sbin/dhclient3"
[   12.063304] type=1505 audit(1295815100.647:3):  operation="profile_load" pid=694 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.063539] type=1505 audit(1295815100.647:4):  operation="profile_load" pid=694 name="/usr/lib/connman/scripts/dhclient-script"
[   12.063861] type=1505 audit(1295815100.647:5):  operation="profile_replace" pid=710 name="/sbin/dhclient3"
[   12.064296] type=1505 audit(1295815100.647:6):  operation="profile_replace" pid=710 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.064541] type=1505 audit(1295815100.647:7):  operation="profile_replace" pid=710 name="/usr/lib/connman/scripts/dhclient-script"
[   12.132865] type=1505 audit(1295815100.717:8):  operation="profile_load" pid=768 name="/usr/share/gdm/guest-session/Xsession"
[   12.137057] type=1505 audit(1295815100.717:9):  operation="profile_replace" pid=769 name="/sbin/dhclient3"
[   12.137482] type=1505 audit(1295815100.717:10):  operation="profile_replace" pid=769 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.137723] type=1505 audit(1295815100.717:11):  operation="profile_replace" pid=769 name="/usr/lib/connman/scripts/dhclient-script"
[   12.477155] Bluetooth: L2CAP ver 2.14
[   12.477159] Bluetooth: L2CAP socket layer initialized
[   12.557371] lp: driver loaded but no devices found
[   13.814951] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   13.830352] EDAC MC: Ver: 2.1.0 Dec  2 2010
[   13.830571] Linux video capture interface: v2.00
[   13.837169] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (174f:1410)
[   13.842449] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.842455] Disabling lock debugging due to kernel taint
[   13.856757] vga16fb: initializing
[   13.856762] vga16fb: mapped to 0xffff8800000a0000
[   13.856839] fb0: VGA16 VGA frame buffer device
[   13.867755] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.867767] wl 0000:03:00.0: setting latency timer to 64
[   13.869322] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input6
[   13.874514] usbcore: registered new interface driver uvcvideo
[   13.874519] USB Video Class driver (v0.1.0)
[   13.881894] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.881899] Bluetooth: BNEP filters: protocol multicast
[   13.976198] [fglrx] Maximum main memory to use for locked dma buffers: 3552 MBytes.
[   13.976241] [fglrx]   vendor: 1002 device: 9712 count: 1
[   13.976638] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   13.976658] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.976665] pci 0000:01:05.0: setting latency timer to 64
[   13.977075] [fglrx] Kernel PAT support is enabled
[   13.977104] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   13.992160] ppdev: user-space parallel port driver
[   13.995653] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   13.997571] lib80211_crypt: registered algorithm 'TKIP'
[   14.000828] EDAC amd64_edac:  Ver: 3.2.0 Dec  2 2010
[   14.001470] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   14.048857] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   14.049146] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.049148]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.049150]  (Note that use of the override may cause unknown side effects.)
[   14.049179] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   14.098657] Bridge firewalling registered
[   14.145182] Bluetooth: SCO (Voice Link) ver 0.6
[   14.145185] Bluetooth: SCO socket layer initialized
[   14.161598] Console: switching to colour frame buffer device 80x30
[   14.189088] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.363980] hda_codec: ALC269: BIOS auto-probing.
[   14.364197] hda_codec: connection list not available for 0x24
[   14.364512] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[   14.371741] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.371817] HDA Intel 0000:01:05.1: setting latency timer to 64
[   14.860131] [fglrx] ATIF platform detected with notification ID: 0x81
[   14.862717] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xa40000
[   14.926364] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.937763] [fglrx] GART Table is not in FRAME_BUFFER range 
[   14.938082]   alloc irq_desc for 27 on node 0
[   14.938085]   alloc kstat_irqs on node 0
[   14.938097] fglrx_pci 0000:01:05.0: irq 27 for MSI/MSI-X
[   14.938884] [fglrx] Firegl kernel thread PID: 1202
[   14.939276] [fglrx] IRQ 27 Enabled
[   15.143492] [fglrx] Gart USWC size:1158 M.
[   15.143497] [fglrx] Gart cacheable size:459 M.
[   15.143504] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   15.143508] [fglrx] Reserved FB block: Unshared offset:14ffb000, size:5000 
[   19.701049] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   42.979458] usb 3-5: USB disconnect, address 2
[   42.980112] btusb_bulk_complete: hci0 urb ffff88012d89e000 failed to resubmit (19)
[   42.980123] btusb_intr_complete: hci0 urb ffff88012d89e6c0 failed to resubmit (19)
[   42.981163] btusb_bulk_complete: hci0 urb ffff88012d89e840 failed to resubmit (19)
[   42.981243] btusb_send_frame: hci0 urb ffff880121e08900 submission failed
[   49.400117] usb 3-5: new full speed USB device using ohci_hcd and address 3
[   49.610413] usb 3-5: configuration #1 chosen from 1 choice
[   49.693437] Bluetooth: RFCOMM TTY layer initialized
[   49.693443] Bluetooth: RFCOMM socket layer initialized
[   49.693446] Bluetooth: RFCOMM ver 1.11
[   67.052076]   alloc irq_desc for 28 on node 0
[   67.052082]   alloc kstat_irqs on node 0
[   67.052098] atl1c 0000:02:00.0: irq 28 for MSI/MSI-X
[   67.053109] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.080301] eth1: no IPv6 routers present
[   85.810902] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   86.010898] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   86.181002] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   86.341019] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   86.433728] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   86.620921] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   87.120649] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   87.410635] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   87.710831] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   87.990880] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   88.272065] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   88.571050] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   88.850704] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   89.130683] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   89.430891] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   89.710612] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   90.620545] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   90.910534] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[   91.545197] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1058.390997] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1059.710675] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1224.140819] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1224.400993] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1224.580803] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1224.760978] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1225.140916] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[ 1225.330809] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD

---

### Post by Krytarik on 2011-01-23
Hi Ale,

.xsession-errors always contains some errors, that is obviously unavoidable. You just have to take care that there are not to much, and not some which are indeed avoidable. I don't see any serious in your log. You have apparently removed or renamed the directories mentioned at the start. And there is an error that the session could not be restored. Maybe from hybernating.

As for dmesg, there are only the messages at the end regarding ACPI which could be relevant. There seems to be a bug in that aspect in some versions of the proprietary ATI/AMD video driver (fglrx).

As long as you don't experience serious failures or misbehaviour, those error are acceptable.

---

### Post by f.pelosa on 2011-01-24
ok, thanks a lot.
I wrote this message since in my last installation of ubuntu (9.04) I never saw a .xsession_errors..

---

