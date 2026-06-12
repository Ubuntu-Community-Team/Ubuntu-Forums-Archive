---
title: "cant start fresh install"
date: 2009-04-24
forum: General Help
---

### Post by infallible on 2009-04-24
I'm trying to install the new version of ubuntu onto my new system, based on a Tyan n3600r. I have one IDE master HDD and one IDE slave optical drive. The installer loads, but when I select the install (or others) option, it goes to a black screen with the flashing underscore cursor in the upper left. and stays there. Tyan tech, before they closed for the night, suggested ubuntu didn't support the boards IDE controller and that I should try a sata drive, but my only sata drive has valuable info on one partition. I haven't fiured out how to get into the RAID config to allow the sata drive to be seen, but tthats another story...

Has anyone encountered this freeze? do I need to adjust BIOS settings, perhaps? I've been really exited about getting this system up and running, and hate to see it miss right out of the gate.

---

### Post by infallible on 2009-06-07
I had resolved this issue with a little help from Tyan's Tech support. I can't recall what the issue was, but I'm experiencing it again after switching to a new install on a new, larger root drive and (somewhat accidentally) resetting the bios to defaults. I removed the 'quiet splash --' bit from the grub options, and I can see that it is freezing just after loading all of the drives. I was able to install to the new drive and partition it, but booting freezes at this point on the new sata drive's install, AND the old IDE drive install. I've tried disabling and/or unplugging each drive in turn (a total of one ide optical, one usb optical, one bootable sata, one non-bootable sata, and one IDE) with no success. Since the kernel loads the SATA drives, then the IDE drives, then freezes, I tried disabling the onboard IDE controller but leaving the onboard sata contollers enabled. I am able to boot a live CD this way, and access my SATA drives, but the SATA drives are no longer available to boot from when the IDE controller is disabled. i used the live cd to [enable boot logging]("http://ubuntuforums.org/showthread.php?t=49925") with no result.

Here's the result from /var/log/installer/syslog.  I suspect it may be a memory mapping issue, but only because there are a lot of settings that I don't understand in the bios for that. Sorry about the length of the log, I'm at wits end after pounding my head against a wall all weekend. There are quite a few bits where it looks like the kernel was having trouble deciding on the root partition's filesystem, and therefore did not copy quite a few things. I'm going to try another install from this live session after the post, but perhaps someone can make sense of this.


```
Jun  6 19:31:17 ubuntu syslogd 1.5.0#5ubuntu3: restart.
Jun  6 19:31:17 ubuntu kernel: Inspecting /boot/System.map-2.6.28-11-generic
Jun  6 19:31:17 ubuntu kernel: Cannot find map file.
Jun  6 19:31:17 ubuntu kernel: Loaded 50903 symbols from 37 modules.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
Jun  6 19:31:17 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jun  6 19:31:17 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbf60000 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bbf60000 - 00000000bbf6a000 (ACPI data)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bbf6a000 - 00000000bbf6b000 (ACPI NVS)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bbf6b000 - 00000000c0000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] DMI present.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] last_pfn = 0x180000 max_arch_pfn = 0x3ffffffff
Jun  6 19:31:17 ubuntu kernel: [    0.000000] last_pfn = 0xbbf60 max_arch_pfn = 0x3ffffffff
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun  6 19:31:17 ubuntu kernel: [    0.000000] modified physical RAM map:
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000000ce000 - 0000000000100000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000bbf60000 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000bbf60000 - 00000000bbf6a000 (ACPI data)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000bbf6a000 - 00000000bbf6b000 (ACPI NVS)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000bbf6b000 - 00000000c0000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  modified: 0000000100000000 - 0000000180000000 (usable)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bbf60000
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  0000000000 - 00bbe00000 page 2M
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  00bbe00000 - 00bbf60000 page 4k
Jun  6 19:31:17 ubuntu kernel: [    0.000000] kernel direct mapping tables up to bbf60000 @ 10000-15000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] last_map_addr: bbf60000 end: bbf60000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000180000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  0100000000 - 0180000000 page 2M
Jun  6 19:31:17 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 180000000 @ 13000-1a000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] last_map_addr: 180000000 end: 180000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] RAMDISK: 7f835000 - 7ffff0cd
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: RSDP 000F7620, 0024 (r2 PTLTD )
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: XSDT BBF6596B, 004C (r1 PTLTD  ^I XSDT    6040000  LTP        0)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: FACP BBF69892, 00F4 (r3 NVIDIA CK8S      6040000 PTL_    F4240)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: DSDT BBF659B7, 3E67 (r1 NVIDIA      CK8  6040000 MSFT  3000000)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: FACS BBF6AFC0, 0040
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: SSDT BBF69986, 0574 (r1 AMD    POWERNOW  6040000 AMD         1)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: SPCR BBF69EFA, 0050 (r1 PTLTD  $UCRTBL$  6040000 PTL         1)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: APIC BBF69F4A, 008E (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: BOOT BBF69FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0180000000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #3 [007f835000 - 007ffff0cd]          RAMDISK ==> [007f835000 - 007ffff0cd]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   #6 [0000013000 - 0000015000]          PGTABLE ==> [0000013000 - 0000015000]
Jun  6 19:31:17 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f7650] 000f7650
Jun  6 19:31:17 ubuntu kernel: [    0.000000]  [ffffe20000000000-ffffe200053fffff] PMD -> [ffff880028200000-ffff88002d5fffff] on node 0
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00180000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jun  6 19:31:17 ubuntu kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun  6 19:31:17 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Jun  6 19:31:17 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000bbf60
Jun  6 19:31:17 ubuntu kernel: [    0.000000]     0: 0x00100000 -> 0x00180000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] On node 0 totalpages: 1294061
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA zone: 2545 pages reserved
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA zone: 1380 pages, LIFO batch:0
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   DMA32 zone: 751512 pages, LIFO batch:31
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Normal zone: 7168 pages used for memmap
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Normal zone: 517120 pages, LIFO batch:31
Jun  6 19:31:17 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun  6 19:31:17 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  6 19:31:17 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 0000000000100000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bbf60000 - 00000000bbf6a000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bbf6a000 - 00000000bbf6b000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bbf6b000 - 00000000c0000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
Jun  6 19:31:17 ubuntu kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1270012
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Initializing CPU#0
Jun  6 19:31:17 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Jun  6 19:31:17 ubuntu kernel: [    0.000000] TSC: Unable to calibrate against PIT
Jun  6 19:31:17 ubuntu kernel: [    0.000000] TSC: using PMTIMER reference calibration
Jun  6 19:31:17 ubuntu kernel: [    0.000000] Detected 2799.960 MHz processor.
Jun  6 19:31:17 ubuntu kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Jun  6 19:31:17 ubuntu kernel: [    0.004000] console [tty0] enabled
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] allocated 62914560 bytes of page_cgroup
Jun  6 19:31:17 ubuntu kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Checking aperture...
Jun  6 19:31:17 ubuntu kernel: [    0.004000] No AGP bridge found
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Node 0: aperture @ bc000000 size 64 MB
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Node 1: aperture @ bc000000 size 64 MB
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Memory: 4997368k/6291456k available (4760k kernel code, 1115212k absent, 178000k reserved, 2540k data, 536k init)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun  6 19:31:17 ubuntu kernel: [    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.92 BogoMIPS (lpj=11199840)
Jun  6 19:31:17 ubuntu kernel: [    0.004032] Security Framework initialized
Jun  6 19:31:17 ubuntu kernel: [    0.004040] SELinux:  Disabled at boot.
Jun  6 19:31:17 ubuntu kernel: [    0.004056] AppArmor: AppArmor initialized
Jun  6 19:31:17 ubuntu kernel: [    0.004065] Mount-cache hash table entries: 256
Jun  6 19:31:17 ubuntu kernel: [    0.004211] Initializing cgroup subsys ns
Jun  6 19:31:17 ubuntu kernel: [    0.004214] Initializing cgroup subsys cpuacct
Jun  6 19:31:17 ubuntu kernel: [    0.004216] Initializing cgroup subsys memory
Jun  6 19:31:17 ubuntu kernel: [    0.004220] Initializing cgroup subsys freezer
Jun  6 19:31:17 ubuntu kernel: [    0.004233] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004235] CPU: L2 Cache: 1024K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004237] tseg: 00bbf80000
Jun  6 19:31:17 ubuntu kernel: [    0.004238] CPU: Physical Processor ID: 0
Jun  6 19:31:17 ubuntu kernel: [    0.004239] CPU: Processor Core ID: 0
Jun  6 19:31:17 ubuntu kernel: [    0.004242] using C1E aware idle routine
Jun  6 19:31:17 ubuntu kernel: [    0.005677] ACPI: Core revision 20080926
Jun  6 19:31:17 ubuntu kernel: [    0.007831] ACPI: Checking initramfs for custom DSDT
Jun  6 19:31:17 ubuntu kernel: [    0.224057] Setting APIC routing to flat
Jun  6 19:31:17 ubuntu kernel: [    0.224537] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Jun  6 19:31:17 ubuntu kernel: [    0.265595] CPU0: Dual-Core AMD Opteron(tm) Processor 2220 SE stepping 02
Jun  6 19:31:17 ubuntu kernel: [    0.268001] Booting processor 1 APIC 0x1 ip 0x6000
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Initializing CPU#1
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5600.35 BogoMIPS (lpj=11200715)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Jun  6 19:31:17 ubuntu kernel: [    0.352215] CPU1: Dual-Core AMD Opteron(tm) Processor 2220 SE stepping 02
Jun  6 19:31:17 ubuntu kernel: [    0.352288] Booting processor 2 APIC 0x2 ip 0x6000
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Initializing CPU#2
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5600.36 BogoMIPS (lpj=11200725)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 1
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 0
Jun  6 19:31:17 ubuntu kernel: [    0.440211] CPU2: Dual-Core AMD Opteron(tm) Processor 2220 SE stepping 02
Jun  6 19:31:17 ubuntu kernel: [    0.440284] Booting processor 3 APIC 0x3 ip 0x6000
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Initializing CPU#3
Jun  6 19:31:17 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5600.36 BogoMIPS (lpj=11200722)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 1
Jun  6 19:31:17 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Jun  6 19:31:17 ubuntu kernel: [    0.528208] CPU3: Dual-Core AMD Opteron(tm) Processor 2220 SE stepping 02
Jun  6 19:31:17 ubuntu kernel: [    0.528218] Brought up 4 CPUs
Jun  6 19:31:17 ubuntu kernel: [    0.528220] Total of 4 processors activated (22401.00 BogoMIPS).
Jun  6 19:31:17 ubuntu kernel: [    0.528308] CPU0 attaching sched-domain:
Jun  6 19:31:17 ubuntu kernel: [    0.528310]  domain 0: span 0-3 level CPU
Jun  6 19:31:17 ubuntu kernel: [    0.528312]   groups: 0 1 2 3
Jun  6 19:31:17 ubuntu kernel: [    0.528317] CPU1 attaching sched-domain:
Jun  6 19:31:17 ubuntu kernel: [    0.528318]  domain 0: span 0-3 level CPU
Jun  6 19:31:17 ubuntu kernel: [    0.528319]   groups: 1 2 3 0
Jun  6 19:31:17 ubuntu kernel: [    0.528322] CPU2 attaching sched-domain:
Jun  6 19:31:17 ubuntu kernel: [    0.528323]  domain 0: span 0-3 level CPU
Jun  6 19:31:17 ubuntu kernel: [    0.528324]   groups: 2 3 0 1
Jun  6 19:31:17 ubuntu kernel: [    0.528327] CPU3 attaching sched-domain:
Jun  6 19:31:17 ubuntu kernel: [    0.528328]  domain 0: span 0-3 level CPU
Jun  6 19:31:17 ubuntu kernel: [    0.528329]   groups: 3 0 1 2
Jun  6 19:31:17 ubuntu kernel: [    0.528405] net_namespace: 1400 bytes
Jun  6 19:31:17 ubuntu kernel: [    0.528405] Booting paravirtualized kernel on bare hardware
Jun  6 19:31:17 ubuntu kernel: [    0.528405] Time: 19:29:28  Date: 06/06/09
Jun  6 19:31:17 ubuntu kernel: [    0.528405] regulator: core version 0.5
Jun  6 19:31:17 ubuntu kernel: [    0.528405] NET: Registered protocol family 16
Jun  6 19:31:17 ubuntu kernel: [    0.528405] node 0 link 2: io port [1000, 4fff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] TOM: 00000000bc000000 aka 3008M
Jun  6 19:31:17 ubuntu kernel: [    0.528405] node 0 link 2: mmio [c0000000, dfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] node 0 link 2: mmio [a0000, bffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] node 0 link 2: mmio [e0000000, e7ffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] TOM2: 0000000180000000 aka 6144M
Jun  6 19:31:17 ubuntu kernel: [    0.528405] bus: [00,7f] on node 0 link 2
Jun  6 19:31:17 ubuntu kernel: [    0.528405] bus: 00 index 0 io port: [0, ffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] bus: 00 index 1 mmio: [bc000000, ffffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] bus: 00 index 2 mmio: [a0000, bffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] bus: 00 index 3 mmio: [180000000, fcffffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.528405] ACPI: bus type pci registered
Jun  6 19:31:17 ubuntu kernel: [    0.528405] PCI: Using configuration type 1 for base access
Jun  6 19:31:17 ubuntu kernel: [    0.528711] ACPI: EC: Look up EC in DSDT
Jun  6 19:31:17 ubuntu kernel: [    0.533803] ACPI: Interpreter enabled
Jun  6 19:31:17 ubuntu kernel: [    0.533805] ACPI: (supports S0 S1 S4 S5)
Jun  6 19:31:17 ubuntu kernel: [    0.533817] ACPI: Using IOAPIC for interrupt routing
Jun  6 19:31:17 ubuntu kernel: [    0.538104] ACPI: No dock devices found.
Jun  6 19:31:17 ubuntu kernel: [    0.538113] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  6 19:31:17 ubuntu kernel: [    0.538264] pci 0000:00:01.0: reg 10 io port: [0x1c00-0x1c7f]
Jun  6 19:31:17 ubuntu kernel: [    0.538275] HPET not enabled in BIOS. You might try hpet=force boot option
Jun  6 19:31:17 ubuntu kernel: [    0.538296] pci 0000:00:01.1: reg 10 io port: [0x2000-0x203f]
Jun  6 19:31:17 ubuntu kernel: [    0.538305] pci 0000:00:01.1: reg 20 io port: [0x2440-0x247f]
Jun  6 19:31:17 ubuntu kernel: [    0.538308] pci 0000:00:01.1: reg 24 io port: [0x2400-0x243f]
Jun  6 19:31:17 ubuntu kernel: [    0.538318] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538322] pci 0000:00:01.1: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538342] pci 0000:00:02.0: reg 10 32bit mmio: [0xc0040000-0xc0040fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538355] pci 0000:00:02.0: supports D1 D2
Jun  6 19:31:17 ubuntu kernel: [    0.538356] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538359] pci 0000:00:02.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538373] pci 0000:00:02.1: reg 10 32bit mmio: [0xc0041000-0xc00410ff]
Jun  6 19:31:17 ubuntu kernel: [    0.538385] pci 0000:00:02.1: supports D1 D2
Jun  6 19:31:17 ubuntu kernel: [    0.538386] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538388] pci 0000:00:02.1: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538409] pci 0000:00:05.0: reg 10 io port: [0x56002430-0x56002437]
Jun  6 19:31:17 ubuntu kernel: [    0.538412] pci 0000:00:05.0: reg 14 io port: [0x24b4-0x24b7]
Jun  6 19:31:17 ubuntu kernel: [    0.538414] pci 0000:00:05.0: reg 18 io port: [0x24b8-0x24bf]
Jun  6 19:31:17 ubuntu kernel: [    0.538417] pci 0000:00:05.0: reg 1c io port: [0x24b0-0x24b3]
Jun  6 19:31:17 ubuntu kernel: [    0.538419] pci 0000:00:05.0: reg 20 io port: [0x2480-0x248f]
Jun  6 19:31:17 ubuntu kernel: [    0.538422] pci 0000:00:05.0: reg 24 32bit mmio: [0xc0042000-0xc0042fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538441] pci 0000:00:05.1: reg 10 io port: [0x24d8-0x24df]
Jun  6 19:31:17 ubuntu kernel: [    0.538444] pci 0000:00:05.1: reg 14 io port: [0x24cc-0x24cf]
Jun  6 19:31:17 ubuntu kernel: [    0.538446] pci 0000:00:05.1: reg 18 io port: [0x24d0-0x24d7]
Jun  6 19:31:17 ubuntu kernel: [    0.538449] pci 0000:00:05.1: reg 1c io port: [0x24c8-0x24cb]
Jun  6 19:31:17 ubuntu kernel: [    0.538451] pci 0000:00:05.1: reg 20 io port: [0x2490-0x249f]
Jun  6 19:31:17 ubuntu kernel: [    0.538454] pci 0000:00:05.1: reg 24 32bit mmio: [0xc0043000-0xc0043fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538473] pci 0000:00:05.2: reg 10 io port: [0x24f0-0x24f7]
Jun  6 19:31:17 ubuntu kernel: [    0.538476] pci 0000:00:05.2: reg 14 io port: [0x24e4-0x24e7]
Jun  6 19:31:17 ubuntu kernel: [    0.538478] pci 0000:00:05.2: reg 18 io port: [0x24e8-0x24ef]
Jun  6 19:31:17 ubuntu kernel: [    0.538481] pci 0000:00:05.2: reg 1c io port: [0x24e0-0x24e3]
Jun  6 19:31:17 ubuntu kernel: [    0.538483] pci 0000:00:05.2: reg 20 io port: [0x24a0-0x24af]
Jun  6 19:31:17 ubuntu kernel: [    0.538486] pci 0000:00:05.2: reg 24 32bit mmio: [0xc0044000-0xc0044fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538533] pci 0000:00:08.0: reg 10 32bit mmio: [0xc0045000-0xc0045fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538536] pci 0000:00:08.0: reg 14 io port: [0x24f8-0x24ff]
Jun  6 19:31:17 ubuntu kernel: [    0.538539] pci 0000:00:08.0: reg 18 32bit mmio: [0xc0041800-0xc00418ff]
Jun  6 19:31:17 ubuntu kernel: [    0.538542] pci 0000:00:08.0: reg 1c 32bit mmio: [0xc0041400-0xc004140f]
Jun  6 19:31:17 ubuntu kernel: [    0.538550] pci 0000:00:08.0: supports D1 D2
Jun  6 19:31:17 ubuntu kernel: [    0.538551] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538554] pci 0000:00:08.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538578] pci 0000:00:09.0: reg 10 32bit mmio: [0xc0047000-0xc0047fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538581] pci 0000:00:09.0: reg 14 io port: [0x2800-0x2807]
Jun  6 19:31:17 ubuntu kernel: [    0.538583] pci 0000:00:09.0: reg 18 32bit mmio: [0xc0046000-0xc00460ff]
Jun  6 19:31:17 ubuntu kernel: [    0.538586] pci 0000:00:09.0: reg 1c 32bit mmio: [0xc0041c00-0xc0041c0f]
Jun  6 19:31:17 ubuntu kernel: [    0.538594] pci 0000:00:09.0: supports D1 D2
Jun  6 19:31:17 ubuntu kernel: [    0.538596] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538599] pci 0000:00:09.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538618] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538619] pci 0000:00:0a.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538638] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538640] pci 0000:00:0d.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538657] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  6 19:31:17 ubuntu kernel: [    0.538659] pci 0000:00:0f.0: PME# disabled
Jun  6 19:31:17 ubuntu kernel: [    0.538782] pci 0000:01:04.0: reg 10 32bit mmio: [0xc8000000-0xcfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538786] pci 0000:01:04.0: reg 14 io port: [0x3000-0x30ff]
Jun  6 19:31:17 ubuntu kernel: [    0.538790] pci 0000:01:04.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538801] pci 0000:01:04.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538806] pci 0000:01:04.0: supports D1 D2
Jun  6 19:31:17 ubuntu kernel: [    0.538827] pci 0000:00:06.0: transparent bridge
Jun  6 19:31:17 ubuntu kernel: [    0.538829] pci 0000:00:06.0: bridge io port: [0x3000-0x3fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538831] pci 0000:00:06.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538833] pci 0000:00:06.0: bridge 32bit mmio pref: [0xc8000000-0xcfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538901] pci 0000:04:00.0: reg 10 32bit mmio: [0xc1000000-0xc1ffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538907] pci 0000:04:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538912] pci 0000:04:00.0: reg 1c 64bit mmio: [0xc2000000-0xc3ffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538916] pci 0000:04:00.0: reg 24 io port: [0x4000-0x407f]
Jun  6 19:31:17 ubuntu kernel: [    0.538919] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538950] pci 0000:00:0f.0: bridge io port: [0x4000-0x4fff]
Jun  6 19:31:17 ubuntu kernel: [    0.538952] pci 0000:00:0f.0: bridge 32bit mmio: [0xc1000000-0xc3ffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538955] pci 0000:00:0f.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.538961] bus 00 -> node 0
Jun  6 19:31:17 ubuntu kernel: [    0.538965] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  6 19:31:17 ubuntu kernel: [    0.539016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
Jun  6 19:31:17 ubuntu kernel: [    0.539030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
Jun  6 19:31:17 ubuntu kernel: [    0.539050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
Jun  6 19:31:17 ubuntu kernel: [    0.539069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR5._PRT]
Jun  6 19:31:17 ubuntu kernel: [    0.556177] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.556336] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.556488] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.556639] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.556791] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.556943] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 *10 11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.557094] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.557245] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.557397] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.557549] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 *10 11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.557701] ACPI: PCI Interrupt Link [LMA2] (IRQs 5 7 10 *11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.557852] ACPI: PCI Interrupt Link [LUS2] (IRQs *5 7 10 11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.558007] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 *10 11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.558159] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.558310] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 10 11 14 15 16 17 18 19 20 21 22 23) *0, disabled.
Jun  6 19:31:17 ubuntu kernel: [    0.558463] ACPI: PCI Interrupt Link [LTID] (IRQs 5 7 10 *11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.558614] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 *10 11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.558766] ACPI: PCI Interrupt Link [LSI2] (IRQs 5 7 10 *11 14 15 16 17 18 19 20 21 22 23)
Jun  6 19:31:17 ubuntu kernel: [    0.558913] ACPI: WMI: Mapper loaded
Jun  6 19:31:17 ubuntu kernel: [    0.558960] SCSI subsystem initialized
Jun  6 19:31:17 ubuntu kernel: [    0.558960] libata version 3.00 loaded.
Jun  6 19:31:17 ubuntu kernel: [    0.558960] usbcore: registered new interface driver usbfs
Jun  6 19:31:17 ubuntu kernel: [    0.558960] usbcore: registered new interface driver hub
Jun  6 19:31:17 ubuntu kernel: [    0.558960] usbcore: registered new device driver usb
Jun  6 19:31:17 ubuntu kernel: [    0.558960] PCI: Using ACPI for IRQ routing
Jun  6 19:31:17 ubuntu kernel: [    0.558960] pci 0000:00:05.0: BAR 0: can't allocate resource
Jun  6 19:31:17 ubuntu kernel: [    0.572010] Bluetooth: Core ver 2.13
Jun  6 19:31:17 ubuntu kernel: [    0.572028] NET: Registered protocol family 31
Jun  6 19:31:17 ubuntu kernel: [    0.572028] Bluetooth: HCI device and connection manager initialized
Jun  6 19:31:17 ubuntu kernel: [    0.572028] Bluetooth: HCI socket layer initialized
Jun  6 19:31:17 ubuntu kernel: [    0.572028] NET: Registered protocol family 8
Jun  6 19:31:17 ubuntu kernel: [    0.572028] NET: Registered protocol family 20
Jun  6 19:31:17 ubuntu kernel: [    0.572029] NetLabel: Initializing
Jun  6 19:31:17 ubuntu kernel: [    0.572030] NetLabel:  domain hash size = 128
Jun  6 19:31:17 ubuntu kernel: [    0.572031] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  6 19:31:17 ubuntu kernel: [    0.572044] NetLabel:  unlabeled traffic allowed by default
Jun  6 19:31:17 ubuntu kernel: [    0.572147] PCI-DMA: Disabling AGP.
Jun  6 19:31:17 ubuntu kernel: [    0.572256] PCI-DMA: aperture base @ bc000000 size 65536 KB
Jun  6 19:31:17 ubuntu kernel: [    0.572258] init_memory_mapping: 00000000bc000000-00000000c0000000
Jun  6 19:31:17 ubuntu kernel: [    0.572260]  00bc000000 - 00c0000000 page 2M
Jun  6 19:31:17 ubuntu kernel: [    0.572266] last_map_addr: c0000000 end: c0000000
Jun  6 19:31:17 ubuntu kernel: [    0.572267] PCI-DMA: using GART IOMMU.
Jun  6 19:31:17 ubuntu kernel: [    0.572272] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun  6 19:31:17 ubuntu kernel: [    0.573312] AppArmor: AppArmor Filesystem Enabled
Jun  6 19:31:17 ubuntu kernel: [    0.584017] pnp: PnP ACPI init
Jun  6 19:31:17 ubuntu kernel: [    0.584038] ACPI: bus type pnp registered
Jun  6 19:31:17 ubuntu kernel: [    0.587706] pnp: PnP ACPI: found 14 devices
Jun  6 19:31:17 ubuntu kernel: [    0.587707] ACPI: ACPI bus type pnp unregistered
Jun  6 19:31:17 ubuntu kernel: [    0.587722] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587724] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587726] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587730] system 00:02: iomem range 0xc0000000-0xc0007fff has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587734] system 00:03: ioport range 0x1000-0x107f has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587736] system 00:03: ioport range 0x1080-0x10ff has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587738] system 00:03: ioport range 0x1400-0x147f has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587739] system 00:03: ioport range 0x1480-0x14ff has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587741] system 00:03: ioport range 0x1800-0x187f has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587743] system 00:03: ioport range 0x1880-0x18ff has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587745] system 00:03: ioport range 0x2440-0x247f has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587746] system 00:03: ioport range 0x2400-0x243f has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587750] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.587752] system 00:06: ioport range 0xc05-0xc06 has been reserved
Jun  6 19:31:17 ubuntu kernel: [    0.592540] pci 0000:00:06.0: PCI bridge, secondary bus 0000:01
Jun  6 19:31:17 ubuntu kernel: [    0.592542] pci 0000:00:06.0:   IO window: 0x3000-0x3fff
Jun  6 19:31:17 ubuntu kernel: [    0.592545] pci 0000:00:06.0:   MEM window: 0xc0100000-0xc01fffff
Jun  6 19:31:17 ubuntu kernel: [    0.592547] pci 0000:00:06.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
Jun  6 19:31:17 ubuntu kernel: [    0.592549] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
Jun  6 19:31:17 ubuntu kernel: [    0.592551] pci 0000:00:0a.0:   IO window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592552] pci 0000:00:0a.0:   MEM window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592554] pci 0000:00:0a.0:   PREFETCH window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592556] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
Jun  6 19:31:17 ubuntu kernel: [    0.592557] pci 0000:00:0d.0:   IO window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592559] pci 0000:00:0d.0:   MEM window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592561] pci 0000:00:0d.0:   PREFETCH window: disabled
Jun  6 19:31:17 ubuntu kernel: [    0.592564] pci 0000:04:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592566] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:04
Jun  6 19:31:17 ubuntu kernel: [    0.592567] pci 0000:00:0f.0:   IO window: 0x4000-0x4fff
Jun  6 19:31:17 ubuntu kernel: [    0.592569] pci 0000:00:0f.0:   MEM window: 0xc1000000-0xc3ffffff
Jun  6 19:31:17 ubuntu kernel: [    0.592571] pci 0000:00:0f.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jun  6 19:31:17 ubuntu kernel: [    0.592578] pci 0000:00:06.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    0.592581] pci 0000:00:0a.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    0.592584] pci 0000:00:0d.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    0.592587] pci 0000:00:0f.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    0.592589] bus: 00 index 0 io port: [0x00-0xffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592591] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592592] bus: 01 index 0 io port: [0x3000-0x3fff]
Jun  6 19:31:17 ubuntu kernel: [    0.592594] bus: 01 index 1 mmio: [0xc0100000-0xc01fffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592595] bus: 01 index 2 mmio: [0xc8000000-0xcfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592596] bus: 01 index 3 io port: [0x00-0xffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592597] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592599] bus: 02 index 0 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592600] bus: 02 index 1 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592601] bus: 02 index 2 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592602] bus: 02 index 3 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592603] bus: 03 index 0 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592604] bus: 03 index 1 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592605] bus: 03 index 2 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592606] bus: 03 index 3 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592607] bus: 04 index 0 io port: [0x4000-0x4fff]
Jun  6 19:31:17 ubuntu kernel: [    0.592609] bus: 04 index 1 mmio: [0xc1000000-0xc3ffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592610] bus: 04 index 2 mmio: [0xd0000000-0xdfffffff]
Jun  6 19:31:17 ubuntu kernel: [    0.592611] bus: 04 index 3 mmio: [0x0-0x0]
Jun  6 19:31:17 ubuntu kernel: [    0.592622] NET: Registered protocol family 2
Jun  6 19:31:17 ubuntu kernel: [    0.596017] Switched to high resolution mode on CPU 0
Jun  6 19:31:17 ubuntu kernel: [    0.596194] Switched to high resolution mode on CPU 1
Jun  6 19:31:17 ubuntu kernel: [    0.596231] Switched to high resolution mode on CPU 3
Jun  6 19:31:17 ubuntu kernel: [    0.596237] Switched to high resolution mode on CPU 2
Jun  6 19:31:17 ubuntu kernel: [    0.632065] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.633603] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.636771] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  6 19:31:17 ubuntu kernel: [    0.637532] TCP: Hash tables configured (established 262144 bind 65536)
Jun  6 19:31:17 ubuntu kernel: [    0.637534] TCP reno registered
Jun  6 19:31:17 ubuntu kernel: [    0.648152] NET: Registered protocol family 1
Jun  6 19:31:17 ubuntu kernel: [    0.648260] checking if image is initramfs... it is
Jun  6 19:31:17 ubuntu kernel: [    1.092428] Freeing initrd memory: 7976k freed
Jun  6 19:31:17 ubuntu kernel: [    1.098054] Simple Boot Flag at 0x37 set to 0x80
Jun  6 19:31:17 ubuntu kernel: [    1.098547] audit: initializing netlink socket (disabled)
Jun  6 19:31:17 ubuntu kernel: [    1.098571] type=2000 audit(1244316568.096:1): initialized
Jun  6 19:31:17 ubuntu kernel: [    1.104955] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun  6 19:31:17 ubuntu kernel: [    1.105997] VFS: Disk quotas dquot_6.5.1
Jun  6 19:31:17 ubuntu kernel: [    1.106037] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  6 19:31:17 ubuntu kernel: [    1.106499] fuse init (API version 7.10)
Jun  6 19:31:17 ubuntu kernel: [    1.106550] msgmni has been set to 9777
Jun  6 19:31:17 ubuntu kernel: [    1.106780] alg: No test for stdrng (krng)
Jun  6 19:31:17 ubuntu kernel: [    1.106799] io scheduler noop registered
Jun  6 19:31:17 ubuntu kernel: [    1.106801] io scheduler anticipatory registered
Jun  6 19:31:17 ubuntu kernel: [    1.106802] io scheduler deadline registered
Jun  6 19:31:17 ubuntu kernel: [    1.106831] io scheduler cfq registered (default)
Jun  6 19:31:17 ubuntu kernel: [    1.106865] pci 0000:00:00.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309331] pci 0000:00:05.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309345] pci 0000:00:05.1: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309358] pci 0000:00:05.2: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309370] pci 0000:00:06.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309386] pci 0000:00:08.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309401] pci 0000:00:09.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309414] pci 0000:00:0a.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309428] pci 0000:00:0d.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309442] pci 0000:00:0f.0: Enabling HT MSI Mapping
Jun  6 19:31:17 ubuntu kernel: [    1.309469] pci 0000:04:00.0: Boot video device
Jun  6 19:31:17 ubuntu kernel: [    1.312254] pcieport-driver 0000:00:0a.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    1.312274] pcieport-driver 0000:00:0a.0: found MSI capability
Jun  6 19:31:17 ubuntu kernel: [    1.312293] pcieport-driver 0000:00:0a.0: irq 2303 for MSI/MSI-X
Jun  6 19:31:17 ubuntu kernel: [    1.312299] pci_express 0000:00:0a.0:pcie00: allocate port service
Jun  6 19:31:17 ubuntu kernel: [    1.312329] pcieport-driver 0000:00:0d.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    1.312346] pcieport-driver 0000:00:0d.0: found MSI capability
Jun  6 19:31:17 ubuntu kernel: [    1.312356] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
Jun  6 19:31:17 ubuntu kernel: [    1.312361] pci_express 0000:00:0d.0:pcie00: allocate port service
Jun  6 19:31:17 ubuntu kernel: [    1.312388] pcieport-driver 0000:00:0f.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    1.312405] pcieport-driver 0000:00:0f.0: found MSI capability
Jun  6 19:31:17 ubuntu kernel: [    1.312415] pcieport-driver 0000:00:0f.0: irq 2301 for MSI/MSI-X
Jun  6 19:31:17 ubuntu kernel: [    1.312420] pci_express 0000:00:0f.0:pcie00: allocate port service
Jun  6 19:31:17 ubuntu kernel: [    1.312457] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  6 19:31:17 ubuntu kernel: [    1.312463] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  6 19:31:17 ubuntu kernel: [    1.312579] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jun  6 19:31:17 ubuntu kernel: [    1.312581] ACPI: Power Button (FF) [PWRF]
Jun  6 19:31:17 ubuntu kernel: [    1.312611] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jun  6 19:31:17 ubuntu kernel: [    1.312613] ACPI: Power Button (CM) [PWRB]
Jun  6 19:31:17 ubuntu kernel: [    1.312865] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun  6 19:31:17 ubuntu kernel: [    1.312902] processor ACPI_CPU:00: registered as cooling_device0
Jun  6 19:31:17 ubuntu kernel: [    1.312907] ACPI: Processor [C000] (supports 2 throttling states)
Jun  6 19:31:17 ubuntu kernel: [    1.312954] processor ACPI_CPU:01: registered as cooling_device1
Jun  6 19:31:17 ubuntu kernel: [    1.312982] processor ACPI_CPU:02: registered as cooling_device2
Jun  6 19:31:17 ubuntu kernel: [    1.313011] processor ACPI_CPU:03: registered as cooling_device3
Jun  6 19:31:17 ubuntu kernel: [    1.344125] Linux agpgart interface v0.103
Jun  6 19:31:17 ubuntu kernel: [    1.344134] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jun  6 19:31:17 ubuntu kernel: [    1.344220] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  6 19:31:17 ubuntu kernel: [    1.344452] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  6 19:31:17 ubuntu kernel: [    1.345036] brd: module loaded
Jun  6 19:31:17 ubuntu kernel: [    1.345280] loop: module loaded
Jun  6 19:31:17 ubuntu kernel: [    1.345331] Fixed MDIO Bus: probed
Jun  6 19:31:17 ubuntu kernel: [    1.345336] PPP generic driver version 2.4.2
Jun  6 19:31:17 ubuntu kernel: [    1.345379] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun  6 19:31:17 ubuntu kernel: [    1.345403] Driver 'sd' needs updating - please use bus_type methods
Jun  6 19:31:17 ubuntu kernel: [    1.345410] Driver 'sr' needs updating - please use bus_type methods
Jun  6 19:31:17 ubuntu kernel: [    1.345549] sata_nv 0000:00:05.0: version 3.5
Jun  6 19:31:17 ubuntu kernel: [    1.345824] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
Jun  6 19:31:17 ubuntu kernel: [    1.345835] sata_nv 0000:00:05.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
Jun  6 19:31:17 ubuntu kernel: [    1.345837] sata_nv 0000:00:05.0: Using SWNCQ mode
Jun  6 19:31:17 ubuntu kernel: [    1.346000] sata_nv 0000:00:05.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    1.346160] scsi0 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    1.346281] scsi1 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    1.346376] ata1: SATA max UDMA/133 cmd 0x1c80 ctl 0x24b4 bmdma 0x2480 irq 23
Jun  6 19:31:17 ubuntu kernel: [    1.346378] ata2: SATA max UDMA/133 cmd 0x24b8 ctl 0x24b0 bmdma 0x2488 irq 23
Jun  6 19:31:17 ubuntu kernel: [    2.078209] ata1: SATA link down (SStatus 0 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    2.956037] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    2.964326] ata2.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
Jun  6 19:31:17 ubuntu kernel: [    2.964328] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun  6 19:31:17 ubuntu kernel: [    2.980330] ata2.00: configured for UDMA/133
Jun  6 19:31:17 ubuntu kernel: [    2.980437] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
Jun  6 19:31:17 ubuntu kernel: [    2.980510] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun  6 19:31:17 ubuntu kernel: [    2.980522] sd 1:0:0:0: [sda] Write Protect is off
Jun  6 19:31:17 ubuntu kernel: [    2.980524] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  6 19:31:17 ubuntu kernel: [    2.980541] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  6 19:31:17 ubuntu kernel: [    2.980588] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Jun  6 19:31:17 ubuntu kernel: [    2.980597] sd 1:0:0:0: [sda] Write Protect is off
Jun  6 19:31:17 ubuntu kernel: [    2.980599] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  6 19:31:17 ubuntu kernel: [    2.980615] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  6 19:31:17 ubuntu kernel: [    2.980617]  sda: sda1 sda2 < sda5 >
Jun  6 19:31:17 ubuntu kernel: [    3.006316] sd 1:0:0:0: [sda] Attached SCSI disk
Jun  6 19:31:17 ubuntu kernel: [    3.006366] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jun  6 19:31:17 ubuntu kernel: [    3.006636] ACPI: PCI Interrupt Link [LSI1] enabled at IRQ 22
Jun  6 19:31:17 ubuntu kernel: [    3.006647] sata_nv 0000:00:05.1: PCI INT B -> Link[LSI1] -> GSI 22 (level, low) -> IRQ 22
Jun  6 19:31:17 ubuntu kernel: [    3.006649] sata_nv 0000:00:05.1: Using SWNCQ mode
Jun  6 19:31:17 ubuntu kernel: [    3.006776] sata_nv 0000:00:05.1: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    3.006950] scsi2 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    3.007033] scsi3 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    3.007130] ata3: SATA max UDMA/133 cmd 0x24d8 ctl 0x24cc bmdma 0x2490 irq 22
Jun  6 19:31:17 ubuntu kernel: [    3.007132] ata4: SATA max UDMA/133 cmd 0x24d0 ctl 0x24c8 bmdma 0x2498 irq 22
Jun  6 19:31:17 ubuntu kernel: [    3.738225] ata3: SATA link down (SStatus 0 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    4.470206] ata4: SATA link down (SStatus 0 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    4.470444] ACPI: PCI Interrupt Link [LSI2] enabled at IRQ 21
Jun  6 19:31:17 ubuntu kernel: [    4.470451] sata_nv 0000:00:05.2: PCI INT C -> Link[LSI2] -> GSI 21 (level, low) -> IRQ 21
Jun  6 19:31:17 ubuntu kernel: [    4.470453] sata_nv 0000:00:05.2: Using SWNCQ mode
Jun  6 19:31:17 ubuntu kernel: [    4.470562] sata_nv 0000:00:05.2: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    4.470727] scsi4 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    4.470824] scsi5 : sata_nv
Jun  6 19:31:17 ubuntu kernel: [    4.470913] ata5: SATA max UDMA/133 cmd 0x24f0 ctl 0x24e4 bmdma 0x24a0 irq 21
Jun  6 19:31:17 ubuntu kernel: [    4.470915] ata6: SATA max UDMA/133 cmd 0x24e8 ctl 0x24e0 bmdma 0x24a8 irq 21
Jun  6 19:31:17 ubuntu kernel: [    5.202256] ata5: SATA link down (SStatus 0 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    5.934250] ata6: SATA link down (SStatus 0 SControl 300)
Jun  6 19:31:17 ubuntu kernel: [    5.934632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  6 19:31:17 ubuntu kernel: [    5.934857] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
Jun  6 19:31:17 ubuntu kernel: [    5.934864] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
Jun  6 19:31:17 ubuntu kernel: [    5.934871] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    5.934873] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jun  6 19:31:17 ubuntu kernel: [    5.934924] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Jun  6 19:31:17 ubuntu kernel: [    5.934955] ehci_hcd 0000:00:02.1: debug port 1
Jun  6 19:31:17 ubuntu kernel: [    5.934958] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jun  6 19:31:17 ubuntu kernel: [    5.934971] ehci_hcd 0000:00:02.1: irq 20, io mem 0xc0041000
Jun  6 19:31:17 ubuntu kernel: [    5.944029] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Jun  6 19:31:17 ubuntu kernel: [    5.944102] usb usb1: configuration #1 chosen from 1 choice
Jun  6 19:31:17 ubuntu kernel: [    5.944124] hub 1-0:1.0: USB hub found
Jun  6 19:31:17 ubuntu kernel: [    5.944132] hub 1-0:1.0: 10 ports detected
Jun  6 19:31:17 ubuntu kernel: [    5.944217] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  6 19:31:17 ubuntu kernel: [    5.944442] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 19
Jun  6 19:31:17 ubuntu kernel: [    5.944449] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 19 (level, low) -> IRQ 19
Jun  6 19:31:17 ubuntu kernel: [    5.944456] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    5.944458] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jun  6 19:31:17 ubuntu kernel: [    5.944486] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Jun  6 19:31:17 ubuntu kernel: [    5.944507] ohci_hcd 0000:00:02.0: irq 19, io mem 0xc0040000
Jun  6 19:31:17 ubuntu kernel: [    6.002044] usb usb2: configuration #1 chosen from 1 choice
Jun  6 19:31:17 ubuntu kernel: [    6.002059] hub 2-0:1.0: USB hub found
Jun  6 19:31:17 ubuntu kernel: [    6.002069] hub 2-0:1.0: 10 ports detected
Jun  6 19:31:17 ubuntu kernel: [    6.002134] uhci_hcd: USB Universal Host Controller Interface driver
Jun  6 19:31:17 ubuntu kernel: [    6.002187] usbcore: registered new interface driver libusual
Jun  6 19:31:17 ubuntu kernel: [    6.002213] usbcore: registered new interface driver usbserial
Jun  6 19:31:17 ubuntu kernel: [    6.002221] USB Serial support registered for generic
Jun  6 19:31:17 ubuntu kernel: [    6.002228] usbcore: registered new interface driver usbserial_generic
Jun  6 19:31:17 ubuntu kernel: [    6.002230] usbserial: USB Serial Driver core
Jun  6 19:31:17 ubuntu kernel: [    6.002266] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jun  6 19:31:17 ubuntu kernel: [    6.004529] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  6 19:31:17 ubuntu kernel: [    6.004536] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  6 19:31:17 ubuntu kernel: [    6.013540] mice: PS/2 mouse device common for all mice
Jun  6 19:31:17 ubuntu kernel: [    6.049584] rtc_cmos 00:09: RTC can wake from S4
Jun  6 19:31:17 ubuntu kernel: [    6.049613] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
Jun  6 19:31:17 ubuntu kernel: [    6.049641] rtc0: alarms up to one year, y3k, 114 bytes nvram
Jun  6 19:31:17 ubuntu kernel: [    6.049692] device-mapper: uevent: version 1.0.3
Jun  6 19:31:17 ubuntu kernel: [    6.049789] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jun  6 19:31:17 ubuntu kernel: [    6.050068] device-mapper: multipath: version 1.0.5 loaded
Jun  6 19:31:17 ubuntu kernel: [    6.050071] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  6 19:31:17 ubuntu kernel: [    6.050385] cpuidle: using governor ladder
Jun  6 19:31:17 ubuntu kernel: [    6.050419] cpuidle: using governor menu
Jun  6 19:31:17 ubuntu kernel: [    6.050732] TCP cubic registered
Jun  6 19:31:17 ubuntu kernel: [    6.050782] NET: Registered protocol family 10
Jun  6 19:31:17 ubuntu kernel: [    6.051094] lo: Disabled Privacy Extensions
Jun  6 19:31:17 ubuntu kernel: [    6.051290] NET: Registered protocol family 17
Jun  6 19:31:17 ubuntu kernel: [    6.051306] Bluetooth: L2CAP ver 2.11
Jun  6 19:31:17 ubuntu kernel: [    6.051307] Bluetooth: L2CAP socket layer initialized
Jun  6 19:31:17 ubuntu kernel: [    6.051310] Bluetooth: SCO (Voice Link) ver 0.6
Jun  6 19:31:17 ubuntu kernel: [    6.051311] Bluetooth: SCO socket layer initialized
Jun  6 19:31:17 ubuntu kernel: [    6.051369] Bluetooth: RFCOMM socket layer initialized
Jun  6 19:31:17 ubuntu kernel: [    6.051374] Bluetooth: RFCOMM TTY layer initialized
Jun  6 19:31:17 ubuntu kernel: [    6.051375] Bluetooth: RFCOMM ver 1.10
Jun  6 19:31:17 ubuntu kernel: [    6.051455] powernow-k8: Found 1 Dual-Core AMD Opteron(tm) Processor 2220 SE processors (4 cpu cores) (version 2.20.00)
Jun  6 19:31:17 ubuntu kernel: [    6.051514] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0x9
Jun  6 19:31:17 ubuntu kernel: [    6.051516] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xb
Jun  6 19:31:17 ubuntu kernel: [    6.051517] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xd
Jun  6 19:31:17 ubuntu kernel: [    6.051518] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xf
Jun  6 19:31:17 ubuntu kernel: [    6.051520] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x11
Jun  6 19:31:17 ubuntu kernel: [    6.051521] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x11
Jun  6 19:31:17 ubuntu kernel: [    6.051522] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
Jun  6 19:31:17 ubuntu kernel: [    6.051622] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0x7
Jun  6 19:31:17 ubuntu kernel: [    6.051624] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0x9
Jun  6 19:31:17 ubuntu kernel: [    6.051626] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xb
Jun  6 19:31:17 ubuntu kernel: [    6.051627] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xd
Jun  6 19:31:17 ubuntu kernel: [    6.051628] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0xf
Jun  6 19:31:17 ubuntu kernel: [    6.051629] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x11
Jun  6 19:31:17 ubuntu kernel: [    6.051631] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
Jun  6 19:31:17 ubuntu kernel: [    6.051749] powernow-k8: ph2 null fid transition 0x14
Jun  6 19:31:17 ubuntu kernel: [    6.051930] registered taskstats version 1
Jun  6 19:31:17 ubuntu kernel: [    6.052065]   Magic number: 13:391:495
Jun  6 19:31:17 ubuntu kernel: [    6.052169] rtc_cmos 00:09: setting system clock to 2009-06-06 19:29:34 UTC (1244316574)
Jun  6 19:31:17 ubuntu kernel: [    6.052172] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  6 19:31:17 ubuntu kernel: [    6.052173] EDD information not available.
Jun  6 19:31:17 ubuntu kernel: [    6.052217] Freeing unused kernel memory: 536k freed
Jun  6 19:31:17 ubuntu kernel: [    6.052506] Write protecting the kernel read-only data: 6708k
Jun  6 19:31:17 ubuntu kernel: [    6.212142] Floppy drive(s): fd0 is 1.44M
Jun  6 19:31:17 ubuntu kernel: [    6.230435] FDC 0 is a post-1991 82077
Jun  6 19:31:17 ubuntu kernel: [    6.240705] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jun  6 19:31:17 ubuntu kernel: [    6.241067] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 18
Jun  6 19:31:17 ubuntu kernel: [    6.241080] forcedeth 0000:00:08.0: PCI INT A -> Link[LMAC] -> GSI 18 (level, low) -> IRQ 18
Jun  6 19:31:17 ubuntu kernel: [    6.241085] forcedeth 0000:00:08.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    6.241154] nv_probe: set workaround bit for reversed mac addr
Jun  6 19:31:17 ubuntu kernel: [    6.243487] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 0, addr 00:e0:81:76:8c:7e
Jun  6 19:31:17 ubuntu kernel: [    6.243489] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Jun  6 19:31:17 ubuntu kernel: [    6.243779] ACPI: PCI Interrupt Link [LMA2] enabled at IRQ 17
Jun  6 19:31:17 ubuntu kernel: [    6.243787] forcedeth 0000:00:09.0: PCI INT A -> Link[LMA2] -> GSI 17 (level, low) -> IRQ 17
Jun  6 19:31:17 ubuntu kernel: [    6.243790] forcedeth 0000:00:09.0: setting latency timer to 64
Jun  6 19:31:17 ubuntu kernel: [    6.243821] nv_probe: set workaround bit for reversed mac addr
Jun  6 19:31:17 ubuntu kernel: [    6.244655] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:e0:81:76:8c:7f
Jun  6 19:31:17 ubuntu kernel: [    6.244657] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Jun  6 19:31:17 ubuntu kernel: [    6.256563] usb 1-2: new high speed USB device using ehci_hcd and address 2
Jun  6 19:31:17 ubuntu kernel: [    6.408598] usb 1-2: configuration #1 chosen from 1 choice
Jun  6 19:31:17 ubuntu kernel: [    6.412560] Initializing USB Mass Storage driver...
Jun  6 19:31:17 ubuntu kernel: [    6.413374] scsi6 : SCSI emulation for USB Mass Storage devices
Jun  6 19:31:17 ubuntu kernel: [    6.413486] usb-storage: device found at 2
Jun  6 19:31:17 ubuntu kernel: [    6.413490] usbcore: registered new interface driver usb-storage
Jun  6 19:31:17 ubuntu kernel: [    6.413493] USB Mass Storage support registered.
Jun  6 19:31:17 ubuntu kernel: [    6.413496] usb-storage: waiting for device to settle before scanning
Jun  6 19:31:17 ubuntu kernel: [    6.880023] usb 2-8: new full speed USB device using ohci_hcd and address 2
Jun  6 19:31:17 ubuntu kernel: [    7.095129] usb 2-8: configuration #1 chosen from 1 choice
Jun  6 19:31:17 ubuntu kernel: [    7.267254] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun  6 19:31:17 ubuntu kernel: [    7.267257] EXT3-fs: write access will be enabled during recovery.
Jun  6 19:31:17 ubuntu kernel: [    7.312476] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    7.312494] EXT3-fs: recovery complete.
Jun  6 19:31:17 ubuntu kernel: [    7.312858] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [    7.344463] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun  6 19:31:17 ubuntu kernel: [    7.344466] EXT3-fs: write access will be enabled during recovery.
Jun  6 19:31:17 ubuntu kernel: [    7.386015] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    7.386030] EXT3-fs: recovery complete.
Jun  6 19:31:17 ubuntu kernel: [    7.387028] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [    7.400519] usb 2-9: new low speed USB device using ohci_hcd and address 3
Jun  6 19:31:17 ubuntu kernel: [    7.617129] usb 2-9: configuration #1 chosen from 1 choice
Jun  6 19:31:17 ubuntu kernel: [    7.629571] usbcore: registered new interface driver hiddev
Jun  6 19:31:17 ubuntu kernel: [    7.636324] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input3
Jun  6 19:31:17 ubuntu kernel: [    7.665561] generic-usb 0003:046E:5250.0001: input,hidraw0: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:02.0-9/input0
Jun  6 19:31:17 ubuntu kernel: [    7.679791] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.1/input/input4
Jun  6 19:31:17 ubuntu kernel: [    7.717572] generic-usb 0003:046E:5250.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:02.0-9/input1
Jun  6 19:31:17 ubuntu kernel: [    7.717588] usbcore: registered new interface driver usbhid
Jun  6 19:31:17 ubuntu kernel: [    7.717590] usbhid: v2.6:USB HID core driver
Jun  6 19:31:17 ubuntu kernel: [    8.463304] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    8.463318] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [    8.492315] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    8.492329] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [    9.536575] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    9.536590] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [    9.550744] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [    9.550759] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [   10.576566] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [   10.576580] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [   10.589984] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [   10.589998] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [   11.408223] usb-storage: device scan complete
Jun  6 19:31:17 ubuntu kernel: [   11.444666] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42L  SL00 PQ: 0 ANSI: 0
Jun  6 19:31:17 ubuntu kernel: [   11.452136] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  6 19:31:17 ubuntu kernel: [   11.452140] Uniform CD-ROM driver Revision: 3.20
Jun  6 19:31:17 ubuntu kernel: [   11.452642] sr 6:0:0:0: Attached scsi CD-ROM sr0
Jun  6 19:31:17 ubuntu kernel: [   11.453209] sr 6:0:0:0: Attached scsi generic sg1 type 5
Jun  6 19:31:17 ubuntu kernel: [   11.615860] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [   11.615871] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [   11.629303] kjournald starting.  Commit interval 5 seconds
Jun  6 19:31:17 ubuntu kernel: [   11.629319] EXT3-fs: mounted filesystem with ordered data mode.
Jun  6 19:31:17 ubuntu kernel: [   12.328632] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun  6 19:31:17 ubuntu kernel: [   12.440394] ISO 9660 Extensions: RRIP_1991A
Jun  6 19:31:17 ubuntu kernel: [   12.795891] aufs 20080922
Jun  6 19:31:17 ubuntu kernel: [   13.067659] squashfs: version 3.3 (2007/10/31) Phillip Lougher
Jun  6 19:31:17 ubuntu kernel: [   99.739571] udev: starting version 141
Jun  6 19:31:17 ubuntu kernel: [  100.170608] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2440
Jun  6 19:31:17 ubuntu kernel: [  100.170628] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2400
Jun  6 19:31:17 ubuntu kernel: [  100.336161] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3202
Jun  6 19:31:17 ubuntu kernel: [  100.336183] usbcore: registered new interface driver usblp
Jun  6 19:31:17 ubuntu kernel: [  101.060181] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jun  6 19:31:17 ubuntu kernel: [  102.403681] parport_pc 00:0d: reported by Plug and Play ACPI
Jun  6 19:31:17 ubuntu kernel: [  102.403802] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun  6 19:31:17 ubuntu kernel: [  103.339129] ppdev: user-space parallel port driver
Jun  6 19:31:17 ubuntu kernel: [  103.340544] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
Jun  6 19:31:17 ubuntu kernel: [  103.340556] resource map sanity check conflict: 0xff000000 0xffffffff 0xfff80000 0xffffffff reserved
Jun  6 19:31:17 ubuntu kernel: [  103.340565] ------------[ cut here ]------------
Jun  6 19:31:17 ubuntu kernel: [  103.340567] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
Jun  6 19:31:17 ubuntu kernel: [  103.340569] Modules linked in: ck804xrom(+) ppdev psmouse mtd parport_pc joydev parport serio_raw chipreg pcspkr map_funcs usblp i2c_nforce2 k8temp squashfs aufs exportfs nls_cp437 isofs usbhid usb_storage forcedeth floppy fbcon tileblit font bitblit softcursor
Jun  6 19:31:17 ubuntu kernel: [  103.340587] Pid: 2577, comm: modprobe Not tainted 2.6.28-11-generic #42-Ubuntu
Jun  6 19:31:17 ubuntu kernel: [  103.340589] Call Trace:
Jun  6 19:31:17 ubuntu kernel: [  103.340596]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
Jun  6 19:31:17 ubuntu kernel: [  103.340600]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Jun  6 19:31:17 ubuntu kernel: [  103.340602]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Jun  6 19:31:17 ubuntu kernel: [  103.340604]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
Jun  6 19:31:17 ubuntu kernel: [  103.340608]  [<ffffffffa01612db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Jun  6 19:31:17 ubuntu kernel: [  103.340611]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
Jun  6 19:31:17 ubuntu kernel: [  103.340614]  [<ffffffffa01612db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Jun  6 19:31:17 ubuntu kernel: [  103.340617]  [<ffffffffa0167041>] init_ck804xrom+0x41/0x59 [ck804xrom]
Jun  6 19:31:17 ubuntu kernel: [  103.340620]  [<ffffffffa0167000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
Jun  6 19:31:17 ubuntu kernel: [  103.340623]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
Jun  6 19:31:17 ubuntu kernel: [  103.340628]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
Jun  6 19:31:17 ubuntu kernel: [  103.340630]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
Jun  6 19:31:17 ubuntu kernel: [  103.340633]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60
Jun  6 19:31:17 ubuntu kernel: [  103.340635]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230
Jun  6 19:31:17 ubuntu kernel: [  103.340637]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
Jun  6 19:31:17 ubuntu kernel: [  103.340642]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
Jun  6 19:31:17 ubuntu kernel: [  103.340645]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Jun  6 19:31:17 ubuntu kernel: [  103.340647] ---[ end trace 8df06f55084b0677 ]---
Jun  6 19:31:17 ubuntu kernel: [  103.979207] Found: SST 49LF080A
Jun  6 19:31:17 ubuntu kernel: [  103.979217] ck804xrom @fff00000: Found 1 x8 devices at 0x0 in 8-bit bank
Jun  6 19:31:17 ubuntu kernel: [  104.072287] number of JEDEC chips: 1
Jun  6 19:31:17 ubuntu kernel: [  104.072290] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
Jun  6 19:31:25 ubuntu acpid: client connected from 4121[111:120] 
Jun  6 19:31:26 ubuntu bluetoothd[4144]: Bluetooth daemon
Jun  6 19:31:26 ubuntu bluetoothd[4144]: Starting SDP server
Jun  6 19:31:29 ubuntu bluetoothd[4144]: Starting experimental netlink support
Jun  6 19:31:29 ubuntu bluetoothd[4144]: Failed to find Bluetooth netlink family
Jun  6 19:31:30 ubuntu kernel: [  122.181815] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  6 19:31:30 ubuntu kernel: [  122.181818] Bluetooth: BNEP filters: protocol multicast
Jun  6 19:31:31 ubuntu bluetoothd[4144]: bridge pan0 created
Jun  6 19:31:31 ubuntu kernel: [  123.164694] Bridge firewalling registered
Jun  6 19:31:31 ubuntu bluetoothd[4144]: Registered interface org.bluez.Service on path /org/bluez/4144/any
Jun  6 19:31:33 ubuntu hal_lpadmin: Running hal_lpadmin
Jun  6 19:31:33 ubuntu NetworkManager: <info>  starting... 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'forcedeth') 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7f 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth') 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7e 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Jun  6 19:31:33 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Jun  6 19:31:34 ubuntu hal_lpadmin: hal_lpadmin triggered by low-level USB device
Jun  6 19:31:34 ubuntu hal_lpadmin: Getting device ID from the usblp HAL entry ...
Jun  6 19:31:34 ubuntu hal_lpadmin: Device ID for /dev/usb/lp0: MFG:HP;MDL:PHOTOSMART 1215;DES:hp photosmart 1215;CMD:MLC,PCL,PML,BIDI-ECP,ECP18,DW-PCL;
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7e, iface: eth0): not well known
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7f, iface: eth1): not well known
Jun  6 19:31:34 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun  6 19:31:34 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  6 19:31:34 ubuntu hal_lpadmin: Written device ID into HAL database entry: MFG:HP;MDL:PHOTOSMART 1215;DES:hp photosmart 1215;CMD:MLC,PCL,PML,BIDI-ECP,ECP18,DW-PCL;
Jun  6 19:31:35 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  6 19:31:35 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (33493456) ... get_connections.
Jun  6 19:31:35 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (33493456) ... get_connections (managed=false): return empty list.
Jun  6 19:31:35 ubuntu hal_lpadmin: Unable to connect to CUPS: 'httpConnectionEncrypt failed'.  Is CUPS running?
Jun  6 19:31:36 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): bringing up device. 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): preparing device. 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jun  6 19:31:38 ubuntu kernel: [  129.554573] forcedeth 0000:00:09.0: irq 2300 for MSI/MSI-X
Jun  6 19:31:38 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): carrier now ON (device state 2) 
Jun  6 19:31:38 ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jun  6 19:31:38 ubuntu kernel: [  129.558293] forcedeth 0000:00:08.0: irq 2299 for MSI/MSI-X
Jun  6 19:31:38 ubuntu kernel: [  129.558508] eth0: no link during initialization.
Jun  6 19:31:38 ubuntu kernel: [  129.560113] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  6 19:31:39 ubuntu nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7e
Jun  6 19:31:39 ubuntu nm-system-settings: Added default wired connection 'Auto eth1' for /org/freedesktop/Hal/devices/net_00_e0_81_76_8c_7f
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1' 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  dhclient started with pid 4283 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun  6 19:31:39 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jun  6 19:31:39 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jun  6 19:31:39 ubuntu dhclient: All rights reserved.
Jun  6 19:31:39 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun  6 19:31:39 ubuntu dhclient: 
Jun  6 19:31:39 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
Jun  6 19:31:39 ubuntu dhclient: Listening on LPF/eth1/00:e0:81:76:8c:7f
Jun  6 19:31:39 ubuntu dhclient: Sending on   LPF/eth1/00:e0:81:76:8c:7f
Jun  6 19:31:39 ubuntu dhclient: Sending on   Socket/fallback
Jun  6 19:31:40 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun  6 19:31:40 ubuntu acpid: client connected from 4282[0:0] 
Jun  6 19:31:41 ubuntu dhclient: DHCPOFFER of 10.0.0.102 from 10.0.0.5
Jun  6 19:31:41 ubuntu dhclient: DHCPREQUEST of 10.0.0.102 on eth1 to 255.255.255.255 port 67
Jun  6 19:31:41 ubuntu dhclient: DHCPACK of 10.0.0.102 from 10.0.0.5
Jun  6 19:31:41 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jun  6 19:31:41 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun  6 19:31:41 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    address 10.0.0.102 
Jun  6 19:31:41 ubuntu dhclient: bound to 10.0.0.102 -- renewal in 37361 seconds.
Jun  6 19:31:41 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    gateway 10.0.0.5 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    hostname 'ubuntu' 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    nameserver '205.171.3.25' 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    nameserver '205.171.2.25' 
Jun  6 19:31:41 ubuntu NetworkManager: <info>    domain name 'immanetize.info' 
Jun  6 19:31:41 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun  6 19:31:41 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jun  6 19:31:41 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jun  6 19:31:42 ubuntu NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jun  6 19:31:42 ubuntu NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 
Jun  6 19:31:42 ubuntu NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jun  6 19:31:42 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  6 19:31:48 ubuntu kernel: [  139.616018] eth1: no IPv6 routers present
Jun  7 01:31:49 ubuntu ntpdate[4361]: step time server 91.189.94.4 offset 21599.813788 sec
Jun  7 01:31:59 ubuntu ubiquity[4376]: Ubiquity 1.12.12
Jun  7 01:32:06 ubuntu ubiquity[4376]: log-output -t ubiquity laptop-detect
Jun  7 01:32:07 ubuntu ubiquity[4376]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Jun  7 01:32:27 ubuntu ubiquity[4376]: switched to page stepLanguage
Jun  7 01:32:30 ubuntu ubiquity[4376]: switched to page stepLanguage
Jun  7 01:32:45 ubuntu localechooser: info: Language = 'en'
Jun  7 01:32:46 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;kbd=lat0-sun16(utf8)
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jun  7 01:32:46 ubuntu localechooser: info: Default country = 'US'
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  7 01:32:46 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  7 01:32:46 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Jun  7 01:32:47 ubuntu ubiquity[4376]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Jun  7 01:32:47 ubuntu ubiquity[4376]: debconffilter_done: Language (current: Language)
Jun  7 01:32:47 ubuntu ubiquity[4376]: Step_before = stepLanguage
Jun  7 01:32:48 ubuntu ubiquity[4376]: switched to page stepLocation
Jun  7 01:32:58 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jun  7 01:32:58 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  7 01:32:58 ubuntu localechooser: info: Language = 'en'
Jun  7 01:32:58 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;kbd=lat0-sun16(utf8)
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jun  7 01:32:58 ubuntu localechooser: info: Default country = 'US'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jun  7 01:32:58 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  7 01:32:58 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Jun  7 01:32:58 ubuntu ubiquity[4376]: debconffilter_done: Timezone (current: Timezone)
Jun  7 01:32:58 ubuntu ubiquity[4376]: Step_before = stepLocation
Jun  7 01:32:59 ubuntu ubiquity[4376]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jun  7 01:32:59 ubuntu ubiquity[4376]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jun  7 01:32:59 ubuntu ubiquity[4376]: switched to page stepKeyboardConf
Jun  7 01:33:12 ubuntu acpid: client connected from 4282[0:0] 
Jun  7 01:33:20 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Jun  7 01:33:20 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Jun  7 01:33:20 ubuntu ubiquity[4376]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option  -option 
Jun  7 01:33:20 ubuntu ubiquity[4376]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Jun  7 01:33:20 ubuntu ubiquity[4376]: Step_before = stepKeyboardConf
Jun  7 01:33:21 ubuntu kernel: [  233.464026] NTFS driver 2.1.29 [Flags: R/O MODULE].
Jun  7 01:33:21 ubuntu kernel: [  233.611241] JFS: nTxBlock = 8192, nTxLock = 65536
Jun  7 01:33:22 ubuntu kernel: [  234.052618] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jun  7 01:33:22 ubuntu kernel: [  234.054357] SGI XFS Quota Management subsystem
Jun  7 01:33:22 ubuntu kernel: [  234.305539] end_request: I/O error, dev fd0, sector 0
Jun  7 01:33:22 ubuntu kernel: [  234.328033] end_request: I/O error, dev fd0, sector 0
Jun  7 01:33:25 ubuntu kernel: [  237.538828] QNX4 filesystem 0.2.3 registered.
Jun  7 01:33:25 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jun  7 01:33:25 ubuntu kernel: [  237.585815] kjournald starting.  Commit interval 5 seconds
Jun  7 01:33:25 ubuntu kernel: [  237.585830] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:33:25 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:33:25 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:33:25 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:33:25 ubuntu 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:33:25 ubuntu 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:33:25 ubuntu 40lsb: result: /dev/sda1:Ubuntu 9.04 (9.04):Ubuntu:linux
Jun  7 01:33:25 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:33:25 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun  7 01:33:25 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  7 01:33:26 ubuntu kernel: [  237.744925] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.744929] sda2: rw=0, want=4, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.744933] EXT3-fs: unable to read superblock
Jun  7 01:33:26 ubuntu kernel: [  237.748375] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.748378] sda2: rw=0, want=4, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.748382] EXT4-fs: unable to read superblock
Jun  7 01:33:26 ubuntu kernel: [  237.751457] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.751461] sda2: rw=0, want=4, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.751465] EXT2-fs: unable to read superblock
Jun  7 01:33:26 ubuntu kernel: [  237.755143] cramfs: wrong magic
Jun  7 01:33:26 ubuntu kernel: [  237.767890] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.767893] sda2: rw=0, want=66, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.767897] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jun  7 01:33:26 ubuntu kernel: [  237.771164] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jun  7 01:33:26 ubuntu kernel: [  237.774612] FAT: bogus number of reserved sectors
Jun  7 01:33:26 ubuntu kernel: [  237.774621] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:33:26 ubuntu kernel: [  237.784258] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.784261] sda2: rw=0, want=72, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.784267] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.784268] sda2: rw=0, want=128, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.787570] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.787574] sda2: rw=0, want=18, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.787581] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jun  7 01:33:26 ubuntu kernel: [  237.787586] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.787587] sda2: rw=0, want=130, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.787590] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jun  7 01:33:26 ubuntu kernel: [  237.787592] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jun  7 01:33:26 ubuntu kernel: [  237.791848] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.791852] sda2: rw=0, want=8, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.791857] XFS: SB read failed
Jun  7 01:33:26 ubuntu kernel: [  237.795318] FAT: bogus number of reserved sectors
Jun  7 01:33:26 ubuntu kernel: [  237.795322] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:33:26 ubuntu kernel: [  237.798569] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.798572] sda2: rw=0, want=4, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.798575] MINIX-fs: unable to read superblock
Jun  7 01:33:26 ubuntu kernel: [  237.804706] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.804709] sda2: rw=0, want=3, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.804711] hfs: unable to find HFS+ superblock
Jun  7 01:33:26 ubuntu kernel: [  237.808212] qnx4: wrong fsid in superblock.
Jun  7 01:33:26 ubuntu kernel: [  237.811264] You didn't specify the type of your ufs filesystem
Jun  7 01:33:26 ubuntu kernel: [  237.811266] 
Jun  7 01:33:26 ubuntu kernel: [  237.811267] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Jun  7 01:33:26 ubuntu kernel: [  237.811268] 
Jun  7 01:33:26 ubuntu kernel: [  237.811268] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun  7 01:33:26 ubuntu kernel: [  237.811284] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.811286] sda2: rw=0, want=18, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.814312] attempt to access beyond end of device
Jun  7 01:33:26 ubuntu kernel: [  237.814315] sda2: rw=0, want=3, limit=2
Jun  7 01:33:26 ubuntu kernel: [  237.814320] hfs: can't find a HFS filesystem on dev sda2.
Jun  7 01:33:26 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun  7 01:33:26 ubuntu kernel: [  237.846276] kjournald starting.  Commit interval 5 seconds
Jun  7 01:33:26 ubuntu kernel: [  237.846291] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:33:26 ubuntu 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:33:26 ubuntu 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:33:26 ubuntu macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:33:26 ubuntu 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:33:26 ubuntu 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jun  7 01:33:26 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jun  7 01:33:26 ubuntu ubiquity[4376]: Device /dev/sda5 not found in os-prober output
Jun  7 01:33:26 ubuntu last message repeated 5 times
Jun  7 01:33:26 ubuntu ubiquity[4376]: switched to page stepPartAuto
Jun  7 01:33:42 ubuntu ubiquity[4376]: switched to page stepPartAdvanced
Jun  7 01:33:56 ubuntu ubiquity[4376]: switched to page stepPartAdvanced
Jun  7 01:35:53 ubuntu ubiquity[4376]: switched to page stepPartAdvanced
Jun  7 01:36:59 ubuntu last message repeated 3 times
Jun  7 01:37:26 ubuntu ubiquity[4376]: debconffilter_done: Partman (current: Partman)
Jun  7 01:37:26 ubuntu ubiquity[4376]: Step_before = stepPartAdvanced
Jun  7 01:37:27 ubuntu ubiquity[4376]: switched to page stepUserInfo
Jun  7 01:37:46 ubuntu ubiquity[4376]: debconffilter_done: UserSetup (current: UserSetup)
Jun  7 01:37:46 ubuntu ubiquity[4376]: Step_before = stepUserInfo
Jun  7 01:37:47 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jun  7 01:37:47 ubuntu kernel: [  499.208826] kjournald starting.  Commit interval 5 seconds
Jun  7 01:37:47 ubuntu kernel: [  499.208841] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:37:47 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:37:47 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:37:47 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:37:47 ubuntu 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:37:47 ubuntu 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:47 ubuntu 40lsb: result: /dev/sda1:Ubuntu 9.04 (9.04):Ubuntu:linux
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:47 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun  7 01:37:47 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  7 01:37:47 ubuntu kernel: [  499.329248] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.329251] sda2: rw=0, want=4, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.329254] EXT3-fs: unable to read superblock
Jun  7 01:37:47 ubuntu kernel: [  499.332254] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.332259] sda2: rw=0, want=4, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.332263] EXT4-fs: unable to read superblock
Jun  7 01:37:47 ubuntu kernel: [  499.335283] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.335287] sda2: rw=0, want=4, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.335291] EXT2-fs: unable to read superblock
Jun  7 01:37:47 ubuntu kernel: [  499.338283] cramfs: wrong magic
Jun  7 01:37:47 ubuntu kernel: [  499.347451] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.347455] sda2: rw=0, want=66, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.347459] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jun  7 01:37:47 ubuntu kernel: [  499.350753] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jun  7 01:37:47 ubuntu kernel: [  499.353901] FAT: bogus number of reserved sectors
Jun  7 01:37:47 ubuntu kernel: [  499.353903] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:37:47 ubuntu kernel: [  499.363250] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.363254] sda2: rw=0, want=72, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.363260] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.363262] sda2: rw=0, want=128, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.366452] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.366455] sda2: rw=0, want=18, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.366462] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jun  7 01:37:47 ubuntu kernel: [  499.366468] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.366470] sda2: rw=0, want=130, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.366472] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jun  7 01:37:47 ubuntu kernel: [  499.366474] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jun  7 01:37:47 ubuntu kernel: [  499.369597] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.369600] sda2: rw=0, want=8, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.369606] XFS: SB read failed
Jun  7 01:37:47 ubuntu kernel: [  499.372957] FAT: bogus number of reserved sectors
Jun  7 01:37:47 ubuntu kernel: [  499.372962] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:37:47 ubuntu kernel: [  499.376074] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.376077] sda2: rw=0, want=4, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.376081] MINIX-fs: unable to read superblock
Jun  7 01:37:47 ubuntu kernel: [  499.379004] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.379008] sda2: rw=0, want=3, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.379012] hfs: unable to find HFS+ superblock
Jun  7 01:37:47 ubuntu kernel: [  499.382162] qnx4: wrong fsid in superblock.
Jun  7 01:37:47 ubuntu kernel: [  499.385061] You didn't specify the type of your ufs filesystem
Jun  7 01:37:47 ubuntu kernel: [  499.385063] 
Jun  7 01:37:47 ubuntu kernel: [  499.385063] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Jun  7 01:37:47 ubuntu kernel: [  499.385064] 
Jun  7 01:37:47 ubuntu kernel: [  499.385065] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun  7 01:37:47 ubuntu kernel: [  499.385081] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.385083] sda2: rw=0, want=18, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.387955] attempt to access beyond end of device
Jun  7 01:37:47 ubuntu kernel: [  499.387959] sda2: rw=0, want=3, limit=2
Jun  7 01:37:47 ubuntu kernel: [  499.387964] hfs: can't find a HFS filesystem on dev sda2.
Jun  7 01:37:47 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun  7 01:37:47 ubuntu kernel: [  499.416698] kjournald starting.  Commit interval 5 seconds
Jun  7 01:37:47 ubuntu kernel: [  499.416715] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:37:47 ubuntu 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:37:47 ubuntu 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:37:47 ubuntu macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:37:47 ubuntu 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:37:47 ubuntu 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jun  7 01:37:47 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jun  7 01:37:47 ubuntu ubiquity[4376]: filtering out /dev/sda1 as it is to be formatted.
Jun  7 01:37:47 ubuntu ubiquity[4376]: filtering out /dev/sda5 as it is to be formatted.
Jun  7 01:37:47 ubuntu ubiquity[4376]: filtering out /dev/sda6 as it is to be formatted.
Jun  7 01:37:47 ubuntu ubiquity[4376]: debconffilter_done: MigrationAssistant (current: MigrationAssistant)
Jun  7 01:37:47 ubuntu ubiquity[4376]: Step_before = stepUserInfo
Jun  7 01:37:48 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jun  7 01:37:48 ubuntu kernel: [  500.341339] kjournald starting.  Commit interval 5 seconds
Jun  7 01:37:48 ubuntu kernel: [  500.341354] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:37:48 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:37:48 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:37:48 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:37:48 ubuntu 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:37:48 ubuntu 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:48 ubuntu 40lsb: result: /dev/sda1:Ubuntu 9.04 (9.04):Ubuntu:linux
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:48 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun  7 01:37:48 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  7 01:37:48 ubuntu kernel: [  500.464256] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.464259] sda2: rw=0, want=4, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.464263] EXT3-fs: unable to read superblock
Jun  7 01:37:48 ubuntu kernel: [  500.467701] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.467705] sda2: rw=0, want=4, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.467710] EXT4-fs: unable to read superblock
Jun  7 01:37:48 ubuntu kernel: [  500.470975] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.470979] sda2: rw=0, want=4, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.470982] EXT2-fs: unable to read superblock
Jun  7 01:37:48 ubuntu kernel: [  500.474074] cramfs: wrong magic
Jun  7 01:37:48 ubuntu kernel: [  500.483675] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.483678] sda2: rw=0, want=66, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.483682] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jun  7 01:37:48 ubuntu kernel: [  500.487107] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jun  7 01:37:48 ubuntu kernel: [  500.490257] FAT: bogus number of reserved sectors
Jun  7 01:37:48 ubuntu kernel: [  500.490259] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:37:48 ubuntu kernel: [  500.499835] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.499839] sda2: rw=0, want=72, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.499846] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.499847] sda2: rw=0, want=128, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.503051] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.503054] sda2: rw=0, want=18, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.503061] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jun  7 01:37:48 ubuntu kernel: [  500.503067] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.503069] sda2: rw=0, want=130, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.503071] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jun  7 01:37:48 ubuntu kernel: [  500.503074] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jun  7 01:37:48 ubuntu kernel: [  500.506227] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.506231] sda2: rw=0, want=8, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.506236] XFS: SB read failed
Jun  7 01:37:48 ubuntu kernel: [  500.509651] FAT: bogus number of reserved sectors
Jun  7 01:37:48 ubuntu kernel: [  500.509654] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:37:48 ubuntu kernel: [  500.512754] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.512757] sda2: rw=0, want=4, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.512761] MINIX-fs: unable to read superblock
Jun  7 01:37:48 ubuntu kernel: [  500.516038] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.516041] sda2: rw=0, want=3, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.516044] hfs: unable to find HFS+ superblock
Jun  7 01:37:48 ubuntu kernel: [  500.519282] qnx4: wrong fsid in superblock.
Jun  7 01:37:48 ubuntu kernel: [  500.522316] You didn't specify the type of your ufs filesystem
Jun  7 01:37:48 ubuntu kernel: [  500.522318] 
Jun  7 01:37:48 ubuntu kernel: [  500.522318] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Jun  7 01:37:48 ubuntu kernel: [  500.522319] 
Jun  7 01:37:48 ubuntu kernel: [  500.522319] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun  7 01:37:48 ubuntu kernel: [  500.522334] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.522335] sda2: rw=0, want=18, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.525316] attempt to access beyond end of device
Jun  7 01:37:48 ubuntu kernel: [  500.525319] sda2: rw=0, want=3, limit=2
Jun  7 01:37:48 ubuntu kernel: [  500.525325] hfs: can't find a HFS filesystem on dev sda2.
Jun  7 01:37:48 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun  7 01:37:48 ubuntu kernel: [  500.555260] kjournald starting.  Commit interval 5 seconds
Jun  7 01:37:48 ubuntu kernel: [  500.555275] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jun  7 01:37:48 ubuntu 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jun  7 01:37:48 ubuntu 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jun  7 01:37:48 ubuntu macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jun  7 01:37:48 ubuntu 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jun  7 01:37:48 ubuntu 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jun  7 01:37:48 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jun  7 01:37:49 ubuntu ubiquity[4376]: switched to page stepReady
Jun  7 01:38:06 ubuntu ubiquity[4376]: debconffilter_done: Summary (current: Summary)
Jun  7 01:38:06 ubuntu ubiquity[4376]: Step_before = stepReady
Jun  7 01:38:06 ubuntu ubiquity[4376]: progress_loop()
Jun  7 01:38:08 ubuntu kernel: [  519.991069] Adding 4883720k swap on /dev/sda5.  Priority:-1 extents:1 across:4883720k
Jun  7 01:38:08 ubuntu partman: mke2fs 1.41.4 (27-Jan-2009)
Jun  7 01:38:42 ubuntu partman: mke2fs 1.41.4 (27-Jan-2009)
Jun  7 01:42:32 ubuntu kernel: [  783.892920] kjournald starting.  Commit interval 5 seconds
Jun  7 01:42:32 ubuntu kernel: [  783.893094] EXT3 FS on sda1, internal journal
Jun  7 01:42:32 ubuntu kernel: [  783.893104] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:42:32 ubuntu kernel: [  783.980887] kjournald starting.  Commit interval 5 seconds
Jun  7 01:42:32 ubuntu kernel: [  783.981181] EXT3 FS on sda6, internal journal
Jun  7 01:42:32 ubuntu kernel: [  783.981189] EXT3-fs: mounted filesystem with ordered data mode.
Jun  7 01:42:34 ubuntu ubiquity[4376]: debconffilter_done: PartmanCommit (current: None)
Jun  7 01:42:53 ubuntu python: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Jun  7 01:42:53 ubuntu python: keeping language packs for: en
Jun  7 01:43:15 ubuntu python: Not copying bin/keyctl
Jun  7 01:43:17 ubuntu python: Not copying etc/casper.conf
Jun  7 01:43:18 ubuntu python: Not copying etc/request-key.conf


### Roughly 1300 lines of 'not copied' were redacted here.


Jun  7 01:48:29 ubuntu python: Not copying usr/lib/os-probes/mounted/90linux-distro
Jun  7 01:48:29 ubuntu python: Not copying usr/lib/os-probes/mounted/90solaris
Jun  7 01:48:50 ubuntu python: Not copying usr/lib/python2.6/dist-packages/ecryptfs-utils/_libecryptfs.a
Jun  7 01:48:50 ubuntu python: Not copying usr/lib/python2.6/dist-packages/ecryptfs-utils/_libecryptfs.la
Jun  7 01:48:50 ubuntu python: Not copying usr/lib/python2.6/dist-packages/ecryptfs-utils/_libecryptfs.so.0.0.0

Jun  7 01:57:55 ubuntu python: Not copying var/lib/locales/supported.d/de
Jun  7 01:57:55 ubuntu python: Not copying var/lib/locales/supported.d/es
Jun  7 01:57:55 ubuntu python: Not copying var/lib/locales/supported.d/xh
Jun  7 01:58:03 ubuntu localechooser: Generating locales...
Jun  7 01:58:03 ubuntu localechooser:   en_US.UTF-8... 
Jun  7 01:58:03 ubuntu localechooser: up-to-date
Jun  7 01:58:03 ubuntu localechooser: Generation complete.
Jun  7 01:58:03 ubuntu localechooser: Generating locales...
Jun  7 01:58:03 ubuntu localechooser:   en_US.UTF-8... 
Jun  7 01:58:03 ubuntu localechooser: up-to-date
Jun  7 01:58:03 ubuntu localechooser: Generation complete.
Jun  7 01:58:03 ubuntu python: log-output -t ubiquity chroot /target fontconfig-voodoo --auto --force --quiet
Jun  7 01:58:04 ubuntu user-setup: Shadow passwords are now on.
Jun  7 01:58:04 ubuntu user-setup: Adding user `pete' ...
Jun  7 01:58:04 ubuntu user-setup: Adding new group `pete' (1000) ...
Jun  7 01:58:04 ubuntu user-setup: Adding new user `pete' (1000) with group `pete' ...
Jun  7 01:58:05 ubuntu user-setup: Creating home directory `/home/pete' ...
Jun  7 01:58:05 ubuntu user-setup: Copying files from `/etc/skel' ...
Jun  7 01:58:05 ubuntu user-setup: addgroup: The group `lpadmin' already exists as a system group. Exiting.
Jun  7 01:58:05 ubuntu user-setup: Adding group `sambashare' (GID 122) ...
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `adm' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group adm
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `cdrom' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group cdrom
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `dialout' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group dialout
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `lpadmin' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group lpadmin
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `plugdev' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group plugdev
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `sambashare' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group sambashare
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: addgroup: 
Jun  7 01:58:05 ubuntu user-setup: The group `admin' already exists as a system group. Exiting.
Jun  7 01:58:05 ubuntu user-setup: Adding user `pete' to group `admin' ...
Jun  7 01:58:05 ubuntu user-setup: Adding user pete to group admin
Jun  7 01:58:05 ubuntu user-setup: Done.
Jun  7 01:58:05 ubuntu user-setup: Using '/usr/share/libgksu/debian/gconf-defaults.libgksu-sudo' to provide 'libgksu-gconf-defaults'.
Jun  7 01:58:09 ubuntu ubiquity: umount: /target/cdrom: not mounted
Jun  7 01:58:09 ubuntu python: log-output -t ubiquity umount /target/cdrom
Jun  7 01:58:09 ubuntu python: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Jun  7 01:58:09 ubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 7: 
Jun  7 01:58:09 ubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Jun  7 01:58:09 ubuntu ubiquity: 
Jun  7 01:58:09 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:09 ubuntu apt-setup: 
Jun  7 01:58:10 ubuntu apt-setup: Using CD-ROM mount point /cdrom/
Jun  7 01:58:10 ubuntu apt-setup: Identifying.. 
Jun  7 01:58:11 ubuntu apt-setup: [0bf367c002eba16ee14e13d539575701-2]
Jun  7 01:58:11 ubuntu apt-setup: Scanning disc for index files..
Jun  7 01:58:12 ubuntu apt-setup: Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Jun  7 01:58:12 ubuntu apt-setup: Found label 'Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)'
Jun  7 01:58:12 ubuntu apt-setup: This disc is called: 
Jun  7 01:58:12 ubuntu apt-setup: 'Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)'
Jun  7 01:58:12 ubuntu apt-setup: Copying package lists...
Jun  7 01:58:12 ubuntu apt-setup: gpgv: 
Jun  7 01:58:12 ubuntu apt-setup: Signature made Mon 20 Apr 2009 02:29:31 PM UTC using DSA key ID FBB75451
Jun  7 01:58:12 ubuntu apt-setup: gpgv: 
Jun  7 01:58:12 ubuntu apt-setup: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Jun  7 01:58:12 ubuntu apt-setup: 
Jun  7 01:58:12 ubuntu apt-setup: ^MReading Package Indexes... 0%^M^MReading Package Indexes... 2%^M
Jun  7 01:58:12 ubuntu apt-setup: ^MReading Package Indexes... Done^M
Jun  7 01:58:12 ubuntu apt-setup: Writing new source list
Jun  7 01:58:12 ubuntu apt-setup: Source list entries for this disc are:
Jun  7 01:58:12 ubuntu apt-setup: deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
Jun  7 01:58:12 ubuntu apt-setup: Repeat this process for the rest of the CDs in your set.
Jun  7 01:58:12 ubuntu apt-setup: W: Skipping non-exisiting file /cdrom/dists/jaunty/main/binary-amd64/Packages
Jun  7 01:58:12 ubuntu apt-setup: W: Skipping non-exisiting file /cdrom/dists/jaunty/restricted/binary-amd64/Packages
Jun  7 01:58:12 ubuntu apt-setup: Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Translation-en_US
Jun  7 01:58:12 ubuntu apt-setup: Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Translation-en_US
Jun  7 01:58:12 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:12 ubuntu apt-setup: 
Jun  7 01:58:13 ubuntu choose-mirror[20848]: INFO: base system installable from CD; skipping mirror check 
Jun  7 01:58:13 ubuntu choose-mirror[20848]: INFO: falling back to codename jaunty 
Jun  7 01:58:13 ubuntu apt-setup: Get:1 http://us.archive.ubuntu.com jaunty Release.gpg [189B]
Jun  7 01:58:13 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Get:2 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Jun  7 01:58:14 ubuntu apt-setup: Get:3 http://us.archive.ubuntu.com jaunty Release [74.6kB]
Jun  7 01:58:14 ubuntu apt-setup: Get:4 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]
Jun  7 01:58:15 ubuntu apt-setup: Get:5 http://us.archive.ubuntu.com jaunty/main Packages [1251kB]
Jun  7 01:58:17 ubuntu apt-setup: Get:6 http://us.archive.ubuntu.com jaunty/restricted Packages [8858B]
Jun  7 01:58:17 ubuntu apt-setup: Get:7 http://us.archive.ubuntu.com jaunty/main Sources [555kB]
Jun  7 01:58:17 ubuntu apt-setup: Get:8 http://us.archive.ubuntu.com jaunty/restricted Sources [3156B]
Jun  7 01:58:17 ubuntu apt-setup: Get:9 http://us.archive.ubuntu.com jaunty/universe Packages [4732kB]
Jun  7 01:58:25 ubuntu apt-setup: Get:10 http://us.archive.ubuntu.com jaunty/universe Sources [2375kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:11 http://us.archive.ubuntu.com jaunty/multiverse Packages [189kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:12 http://us.archive.ubuntu.com jaunty/multiverse Sources [107kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:13 http://us.archive.ubuntu.com jaunty-updates/main Packages [66.5kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:14 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [14B]
Jun  7 01:58:27 ubuntu apt-setup: Get:15 http://us.archive.ubuntu.com jaunty-updates/main Sources [21.9kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:16 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [14B]
Jun  7 01:58:27 ubuntu apt-setup: Get:17 http://us.archive.ubuntu.com jaunty-updates/universe Packages [19.5kB]
Jun  7 01:58:27 ubuntu apt-setup: Get:18 http://us.archive.ubuntu.com jaunty-updates/universe Sources [5564B]
Jun  7 01:58:27 ubuntu apt-setup: Get:19 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [660B]
Jun  7 01:58:27 ubuntu apt-setup: Get:20 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [639B]
Jun  7 01:58:29 ubuntu apt-setup: Fetched 9460kB in 15s (603kB/s)
Jun  7 01:58:29 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:30 ubuntu apt-setup: 
Jun  7 01:58:30 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:30 ubuntu apt-setup: 
Jun  7 01:58:30 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:30 ubuntu apt-setup: 
Jun  7 01:58:31 ubuntu apt-setup: Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Jun  7 01:58:31 ubuntu apt-setup: Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Jun  7 01:58:31 ubuntu apt-setup: Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Jun  7 01:58:31 ubuntu apt-setup: Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Jun  7 01:58:31 ubuntu apt-setup: Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Jun  7 01:58:31 ubuntu apt-setup: Get:2 http://security.ubuntu.com jaunty-security Release [49.6kB]
Jun  7 01:58:32 ubuntu apt-setup: Get:3 http://security.ubuntu.com jaunty-security/main Packages [24.9kB]
Jun  7 01:58:32 ubuntu apt-setup: Get:4 http://security.ubuntu.com jaunty-security/restricted Packages [14B]
Jun  7 01:58:32 ubuntu apt-setup: Get:5 http://security.ubuntu.com jaunty-security/main Sources [7756B]
Jun  7 01:58:32 ubuntu apt-setup: Get:6 http://security.ubuntu.com jaunty-security/restricted Sources [14B]
Jun  7 01:58:32 ubuntu apt-setup: Get:7 http://security.ubuntu.com jaunty-security/universe Packages [8823B]
Jun  7 01:58:32 ubuntu apt-setup: Get:8 http://security.ubuntu.com jaunty-security/universe Sources [1941B]
Jun  7 01:58:32 ubuntu apt-setup: Get:9 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]
Jun  7 01:58:32 ubuntu apt-setup: Get:10 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]
Jun  7 01:58:32 ubuntu apt-setup: Fetched 93.3kB in 2s (45.2kB/s)
Jun  7 01:58:32 ubuntu apt-setup: Reading package lists...
Jun  7 01:58:32 ubuntu apt-setup: 
Jun  7 01:58:34 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Jun  7 01:58:34 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Jun  7 01:58:35 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Jun  7 01:58:35 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Jun  7 01:58:37 ubuntu kernel: [ 1748.768344] warning: process `rdate' used the deprecated sysctl system call with 1.40.
Jun  7 01:58:41 ubuntu clock-setup: Sun Jun  7 01:58:41 UTC 2009
Jun  7 01:58:41 ubuntu clock-setup: rdate: adjust local clock by -0.027785 seconds
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  7 01:58:41 ubuntu kernel: [ 1753.259491] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.259495] sda2: rw=0, want=4, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.259498] EXT3-fs: unable to read superblock
Jun  7 01:58:41 ubuntu kernel: [ 1753.262495] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.262498] sda2: rw=0, want=4, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.262503] EXT4-fs: unable to read superblock
Jun  7 01:58:41 ubuntu kernel: [ 1753.265351] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.265355] sda2: rw=0, want=4, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.265359] EXT2-fs: unable to read superblock
Jun  7 01:58:41 ubuntu kernel: [ 1753.268242] cramfs: wrong magic
Jun  7 01:58:41 ubuntu kernel: [ 1753.426433] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.426436] sda2: rw=0, want=66, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.426440] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jun  7 01:58:41 ubuntu kernel: [ 1753.430325] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jun  7 01:58:41 ubuntu kernel: [ 1753.433349] FAT: bogus number of reserved sectors
Jun  7 01:58:41 ubuntu kernel: [ 1753.433351] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:58:41 ubuntu kernel: [ 1753.442097] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.442101] sda2: rw=0, want=72, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.442107] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.442109] sda2: rw=0, want=128, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.445128] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.445131] sda2: rw=0, want=18, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.445139] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jun  7 01:58:41 ubuntu kernel: [ 1753.445145] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.445148] sda2: rw=0, want=130, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.445152] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jun  7 01:58:41 ubuntu kernel: [ 1753.445155] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jun  7 01:58:41 ubuntu kernel: [ 1753.448242] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.448245] sda2: rw=0, want=8, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.448250] XFS: SB read failed
Jun  7 01:58:41 ubuntu kernel: [ 1753.451557] FAT: bogus number of reserved sectors
Jun  7 01:58:41 ubuntu kernel: [ 1753.451562] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:58:41 ubuntu kernel: [ 1753.454443] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.454446] sda2: rw=0, want=4, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.454450] MINIX-fs: unable to read superblock
Jun  7 01:58:41 ubuntu kernel: [ 1753.457340] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.457344] sda2: rw=0, want=3, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.457348] hfs: unable to find HFS+ superblock
Jun  7 01:58:41 ubuntu kernel: [ 1753.460396] qnx4: wrong fsid in superblock.
Jun  7 01:58:41 ubuntu kernel: [ 1753.463331] You didn't specify the type of your ufs filesystem
Jun  7 01:58:41 ubuntu kernel: [ 1753.463333] 
Jun  7 01:58:41 ubuntu kernel: [ 1753.463333] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Jun  7 01:58:41 ubuntu kernel: [ 1753.463334] 
Jun  7 01:58:41 ubuntu kernel: [ 1753.463335] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun  7 01:58:41 ubuntu kernel: [ 1753.463350] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.463351] sda2: rw=0, want=18, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.466293] attempt to access beyond end of device
Jun  7 01:58:41 ubuntu kernel: [ 1753.466296] sda2: rw=0, want=3, limit=2
Jun  7 01:58:41 ubuntu kernel: [ 1753.466300] hfs: can't find a HFS filesystem on dev sda2.
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda6
Jun  7 01:58:41 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda6
Jun  7 01:58:41 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda6
Jun  7 01:58:41 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda6
Jun  7 01:58:41 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda6
Jun  7 01:58:41 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda6
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda6
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda6
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda6
Jun  7 01:58:41 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda6
Jun  7 01:58:41 ubuntu hw-detect: FATAL: Module rtc not found.
Jun  7 01:58:41 ubuntu clock-setup: rtc module not loaded
Jun  7 01:58:41 ubuntu hw-detect: FATAL: Module rtc_dev not found.
Jun  7 01:58:41 ubuntu clock-setup: rtc-dev module not loaded
Jun  7 01:58:43 ubuntu clock-setup: hwclock from util-linux-ng 2.14.2
Jun  7 01:58:43 ubuntu clock-setup: Using /dev interface to clock.
Jun  7 01:58:43 ubuntu clock-setup: Assuming hardware clock is kept in local time.
Jun  7 01:58:43 ubuntu clock-setup: Waiting for clock tick...
Jun  7 01:58:43 ubuntu clock-setup: ...got clock tick
Jun  7 01:58:43 ubuntu clock-setup: Time read from Hardware Clock: 2009/06/06 19:58:42
Jun  7 01:58:43 ubuntu clock-setup: Hw clock time : 2009/06/06 19:58:42 = 1244339922 seconds since 1969
Jun  7 01:58:43 ubuntu clock-setup: Time elapsed since reference time has been 0.158960 seconds.
Jun  7 01:58:43 ubuntu clock-setup: Delaying further to reach the next full second.
Jun  7 01:58:43 ubuntu clock-setup: Setting Hardware Clock to 19:58:43 = 1244339923 seconds since 1969
Jun  7 01:58:43 ubuntu clock-setup: ioctl(RTC_SET_TIME) was successful.
Jun  7 01:58:43 ubuntu clock-setup: Not adjusting drift factor because last calibration time is zero,
Jun  7 01:58:43 ubuntu clock-setup: so history is bad and calibration startover is necessary.
Jun  7 01:58:44 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Jun  7 01:58:44 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Jun  7 01:58:46 ubuntu check-missing-firmware: no missing firmware in /tmp/missing-firmware
Jun  7 01:58:46 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Jun  7 01:58:46 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Jun  7 01:58:46 ubuntu python: log-output -t ubiquity /usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer
Jun  7 01:58:47 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Jun  7 01:58:47 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Jun  7 01:58:47 ubuntu python: log-output -t ubiquity mount --bind /tmp/.X11-unix /target/tmp/.X11-unix
Jun  7 01:58:47 ubuntu python: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --add /usr/sbin/update-initramfs
Jun  7 01:58:48 ubuntu ubiquity: Running depmod.
Jun  7 01:58:48 ubuntu ubiquity: Failed to symbolic-link /boot/initrd.img-2.6.28-11-generic to initrd.img.
Jun  7 01:58:50 ubuntu ubiquity: Package `splashy' is not installed and no info is available.
Jun  7 01:58:50 ubuntu ubiquity: Use dpkg --info (= dpkg-deb --info) to examine archive files,
Jun  7 01:58:50 ubuntu ubiquity: and dpkg --contents (= dpkg-deb --contents) to list their contents.
Jun  7 01:58:50 ubuntu ubiquity: /usr/sbin/dpkg-reconfigure: splashy is not installed
Jun  7 01:58:52 ubuntu ubiquity: 
Jun  7 01:58:52 ubuntu ubiquity: Creating config file /etc/papersize with new version
Jun  7 01:58:53 ubuntu ubiquity: /var/lib/dpkg/info/ssl-cert.postinst: 37: 
Jun  7 01:58:53 ubuntu ubiquity: cannot open /etc/ssl/certs/ssl-cert-snakeoil.pem: No such file
Jun  7 01:58:53 ubuntu ubiquity: 
Jun  7 01:58:53 ubuntu ubiquity: /var/lib/dpkg/info/ssl-cert.postinst: 37: 
Jun  7 01:58:53 ubuntu ubiquity: cannot open /etc/ssl/certs/ssl-cert-snakeoil.pem: No such file
Jun  7 01:58:53 ubuntu ubiquity: 
Jun  7 01:58:53 ubuntu python: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --remove /usr/sbin/update-initramfs
Jun  7 01:58:53 ubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity chroot /target update-initramfs -c -k 2.6.28-11-generic
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity umount /target/tmp/.X11-unix
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity mount --bind /proc /target/proc
Jun  7 01:58:59 ubuntu python: log-output -t ubiquity mount --bind /dev /target/dev
Jun  7 01:58:59 ubuntu grub-installer: info: architecture: amd64/generic
Jun  7 01:59:00 ubuntu grub-installer: info: Identified partition label for /dev/sda1: msdos
Jun  7 01:59:00 ubuntu grub-installer: dpkg - warning: ignoring request to remove grub-pc which isn't installed.
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jun  7 01:59:00 ubuntu kernel: [ 1772.148218] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.148221] sda2: rw=0, want=4, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.148225] EXT3-fs: unable to read superblock
Jun  7 01:59:00 ubuntu kernel: [ 1772.151347] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.151352] sda2: rw=0, want=4, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.151356] EXT4-fs: unable to read superblock
Jun  7 01:59:00 ubuntu kernel: [ 1772.154471] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.154475] sda2: rw=0, want=4, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.154479] EXT2-fs: unable to read superblock
Jun  7 01:59:00 ubuntu kernel: [ 1772.157587] cramfs: wrong magic
Jun  7 01:59:00 ubuntu kernel: [ 1772.166893] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.166897] sda2: rw=0, want=66, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.166901] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jun  7 01:59:00 ubuntu kernel: [ 1772.170169] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jun  7 01:59:00 ubuntu kernel: [ 1772.173303] FAT: bogus number of reserved sectors
Jun  7 01:59:00 ubuntu kernel: [ 1772.173308] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:59:00 ubuntu kernel: [ 1772.182970] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.182973] sda2: rw=0, want=72, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.182979] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.182981] sda2: rw=0, want=128, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.186125] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.186129] sda2: rw=0, want=18, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.186136] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jun  7 01:59:00 ubuntu kernel: [ 1772.186142] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.186144] sda2: rw=0, want=130, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.186146] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jun  7 01:59:00 ubuntu kernel: [ 1772.186148] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jun  7 01:59:00 ubuntu kernel: [ 1772.189184] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.189188] sda2: rw=0, want=8, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.189193] XFS: SB read failed
Jun  7 01:59:00 ubuntu kernel: [ 1772.192451] FAT: bogus number of reserved sectors
Jun  7 01:59:00 ubuntu kernel: [ 1772.192455] VFS: Can't find a valid FAT filesystem on dev sda2.
Jun  7 01:59:00 ubuntu kernel: [ 1772.195675] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.195679] sda2: rw=0, want=4, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.195683] MINIX-fs: unable to read superblock
Jun  7 01:59:00 ubuntu kernel: [ 1772.198756] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.198759] sda2: rw=0, want=3, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.198763] hfs: unable to find HFS+ superblock
Jun  7 01:59:00 ubuntu kernel: [ 1772.202073] qnx4: wrong fsid in superblock.
Jun  7 01:59:00 ubuntu kernel: [ 1772.204988] You didn't specify the type of your ufs filesystem
Jun  7 01:59:00 ubuntu kernel: [ 1772.204990] 
Jun  7 01:59:00 ubuntu kernel: [ 1772.204990] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Jun  7 01:59:00 ubuntu kernel: [ 1772.204991] 
Jun  7 01:59:00 ubuntu kernel: [ 1772.204991] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun  7 01:59:00 ubuntu kernel: [ 1772.205038] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.205041] sda2: rw=0, want=18, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.208152] attempt to access beyond end of device
Jun  7 01:59:00 ubuntu kernel: [ 1772.208155] sda2: rw=0, want=3, limit=2
Jun  7 01:59:00 ubuntu kernel: [ 1772.208160] hfs: can't find a HFS filesystem on dev sda2.
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda6
Jun  7 01:59:00 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda6
Jun  7 01:59:00 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda6
Jun  7 01:59:00 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda6
Jun  7 01:59:00 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda6
Jun  7 01:59:00 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda6
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda6
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda6
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda6
Jun  7 01:59:00 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda6
Jun  7 01:59:00 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Jun  7 01:59:00 ubuntu grub-installer: info: grub-install supports --no-floppy
Jun  7 01:59:00 ubuntu grub-installer: info: Running chroot /target grub-install  --no-floppy  "/dev/sda"
Jun  7 01:59:00 ubuntu grub-installer: You shouldn't call /sbin/grub-install. Please call /usr/sbin/grub-install instead!
Jun  7 01:59:00 ubuntu grub-installer: 
Jun  7 01:59:01 ubuntu grub-installer: Probing devices to guess BIOS drives. This may take a long time.
Jun  7 01:59:01 ubuntu grub-installer: Searching for GRUB installation directory ... 
Jun  7 01:59:01 ubuntu grub-installer: found: /boot/grub
Jun  7 01:59:06 ubuntu grub-installer: Installing GRUB to /dev/sda as (hd0)...
Jun  7 01:59:06 ubuntu grub-installer: Installation finished. No error reported.
Jun  7 01:59:06 ubuntu grub-installer: This is the contents of the device map /boot/grub/device.map.
Jun  7 01:59:06 ubuntu grub-installer: Check if this is correct or not. If any of the lines is incorrect,
Jun  7 01:59:06 ubuntu grub-installer: fix it and re-run the script `grub-install'.
Jun  7 01:59:06 ubuntu grub-installer: 
Jun  7 01:59:06 ubuntu grub-installer: (hd0)^I/dev/sda
Jun  7 01:59:06 ubuntu grub-installer: info: grub-install ran successfully
Jun  7 01:59:06 ubuntu ubiquity: I: Setting partition 1 of /dev/sda to active...
Jun  7 01:59:06 ubuntu ubiquity: Done
Jun  7 01:59:06 ubuntu ubiquity: 
Jun  7 01:59:06 ubuntu ubiquity: done.
Jun  7 01:59:06 ubuntu grub-installer: Searching for GRUB installation directory ... 
Jun  7 01:59:06 ubuntu grub-installer: found: /boot/grub
Jun  7 01:59:07 ubuntu grub-installer: Searching for default file ... found: /boot/grub/default
Jun  7 01:59:07 ubuntu grub-installer: Testing for an existing GRUB menu.lst file ... 
Jun  7 01:59:07 ubuntu grub-installer: 
Jun  7 01:59:07 ubuntu grub-installer: Could not find /boot/grub/menu.lst file. 
Jun  7 01:59:07 ubuntu grub-installer: Generating /boot/grub/menu.lst
Jun  7 01:59:07 ubuntu grub-installer: Searching for splash image ... 
Jun  7 01:59:07 ubuntu grub-installer: none found, skipping ...
Jun  7 01:59:07 ubuntu grub-installer: Found kernel: /boot/memtest86+.bin
Jun  7 01:59:07 ubuntu grub-installer: Found kernel: /boot/vmlinuz-2.6.28-11-generic
Jun  7 01:59:07 ubuntu grub-installer: Found kernel: /boot/memtest86+.bin
Jun  7 01:59:07 ubuntu grub-installer: Updating /boot/grub/menu.lst ... 
Jun  7 01:59:07 ubuntu grub-installer: done
Jun  7 01:59:07 ubuntu grub-installer: 
Jun  7 01:59:07 ubuntu python: log-output -t ubiquity umount -f /target/proc
Jun  7 01:59:07 ubuntu python: log-output -t ubiquity umount -f /target/dev
Jun  7 01:59:08 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Jun  7 01:59:08 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Jun  7 01:59:08 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Jun  7 01:59:08 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Jun  7 01:59:14 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Jun  7 01:59:14 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Jun  7 01:59:14 ubuntu ubiquity: (Reading database ... 
Jun  7 01:59:14 ubuntu ubiquity: 103509 files and directories currently installed.)
Jun  7 01:59:14 ubuntu ubiquity: Removing lupin-casper ...
Jun  7 01:59:15 ubuntu ubiquity: Removing casper ...
Jun  7 01:59:15 ubuntu ubiquity: Purging configuration files for casper ...
Jun  7 01:59:15 ubuntu ubiquity: Removing gnome-user-guide-de ...
Jun  7 01:59:15 ubuntu ubiquity: Purging configuration files for gnome-user-guide-de ...
Jun  7 01:59:15 ubuntu ubiquity: Removing gnome-user-guide-es ...
Jun  7 01:59:15 ubuntu ubiquity: Purging configuration files for gnome-user-guide-es ...
Jun  7 01:59:15 ubuntu ubiquity: Removing gparted ...
Jun  7 01:59:16 ubuntu ubiquity: Purging configuration files for gparted ...
Jun  7 01:59:16 ubuntu ubiquity: Removing jfsutils ...
Jun  7 01:59:16 ubuntu ubiquity: Removing localechooser-data ...
Jun  7 01:59:16 ubuntu ubiquity: Removing user-setup ...
Jun  7 01:59:16 ubuntu ubiquity: Purging configuration files for user-setup ...
Jun  7 01:59:17 ubuntu ubiquity: Removing xfsprogs ...
Jun  7 01:59:17 ubuntu ubiquity: Purging configuration files for xfsprogs ...
Jun  7 01:59:18 ubuntu ubiquity: Removing language-pack-de-base ...
Jun  7 01:59:18 ubuntu ubiquity: Purging configuration files for language-pack-de-base ...
Jun  7 01:59:18 ubuntu ubiquity: Removing language-pack-es-base ...
Jun  7 01:59:19 ubuntu ubiquity: Purging configuration files for language-pack-es-base ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-gnome-de-base ...
Jun  7 01:59:19 ubuntu ubiquity: Purging configuration files for language-pack-gnome-de-base ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-gnome-es-base ...
Jun  7 01:59:19 ubuntu ubiquity: Purging configuration files for language-pack-gnome-es-base ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-gnome-xh-base ...
Jun  7 01:59:19 ubuntu ubiquity: Purging configuration files for language-pack-gnome-xh-base ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-xh-base ...
Jun  7 01:59:19 ubuntu ubiquity: Purging configuration files for language-pack-xh-base ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-de ...
Jun  7 01:59:19 ubuntu ubiquity: Removing language-pack-es ...
Jun  7 01:59:20 ubuntu ubiquity: Removing language-pack-gnome-de ...
Jun  7 01:59:20 ubuntu ubiquity: Removing language-pack-gnome-es ...
Jun  7 01:59:20 ubuntu ubiquity: Removing language-pack-gnome-xh ...
Jun  7 01:59:20 ubuntu ubiquity: Removing language-pack-xh ...
Jun  7 01:59:20 ubuntu ubiquity: Removing ubiquity ...
Jun  7 01:59:20 ubuntu ubiquity: Purging configuration files for ubiquity ...
Jun  7 01:59:21 ubuntu ubiquity: Removing ubiquity-frontend-gtk ...
Jun  7 01:59:21 ubuntu ubiquity: Removing ecryptfs-utils ...
Jun  7 01:59:22 ubuntu ubiquity: Removing keyutils ...
Jun  7 01:59:22 ubuntu ubiquity: Purging configuration files for keyutils ...
Jun  7 01:59:22 ubuntu ubiquity: Removing libdebconfclient0 ...
Jun  7 01:59:22 ubuntu ubiquity: Purging configuration files for libdebconfclient0 ...
Jun  7 01:59:22 ubuntu ubiquity: Removing libdebian-installer4 ...
Jun  7 01:59:22 ubuntu ubiquity: Purging configuration files for libdebian-installer4 ...
Jun  7 01:59:22 ubuntu ubiquity: Removing libecryptfs0 ...
Jun  7 01:59:22 ubuntu ubiquity: Purging configuration files for libecryptfs0 ...
Jun  7 01:59:22 ubuntu ubiquity: Removing ntfsprogs ...
Jun  7 01:59:22 ubuntu ubiquity: Removing libntfs10 ...
Jun  7 01:59:22 ubuntu ubiquity: Purging configuration files for libntfs10 ...
Jun  7 01:59:23 ubuntu ubiquity: Removing os-prober ...
Jun  7 01:59:23 ubuntu ubiquity: Removing rdate ...
Jun  7 01:59:23 ubuntu ubiquity: Removing ubiquity-casper ...
Jun  7 01:59:23 ubuntu ubiquity: Removing ubiquity-ubuntu-artwork ...
Jun  7 01:59:23 ubuntu ubiquity: Processing triggers for man-db ...
Jun  7 01:59:24 ubuntu ubiquity: Processing triggers for libc6 ...
Jun  7 01:59:24 ubuntu ubiquity: ldconfig deferred processing now taking place
Jun  7 01:59:24 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Jun  7 01:59:24 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Jun  7 01:59:26 ubuntu kernel: [ 1798.178488] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:26 ubuntu kernel: [ 1798.178496] Buffer I/O error on device sr0, logical block 356716
Jun  7 01:59:26 ubuntu kernel: [ 1798.178500] Buffer I/O error on device sr0, logical block 356717
Jun  7 01:59:27 ubuntu kernel: [ 1798.972481] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:27 ubuntu kernel: [ 1798.972483] Buffer I/O error on device sr0, logical block 356716
Jun  7 01:59:27 ubuntu kernel: [ 1798.972486] Buffer I/O error on device sr0, logical block 356717
Jun  7 01:59:27 ubuntu kernel: [ 1799.194105] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:27 ubuntu kernel: [ 1799.194107] Buffer I/O error on device sr0, logical block 356716
Jun  7 01:59:27 ubuntu kernel: [ 1799.194110] Buffer I/O error on device sr0, logical block 356717
Jun  7 01:59:27 ubuntu kernel: [ 1799.415730] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:27 ubuntu kernel: [ 1799.415732] Buffer I/O error on device sr0, logical block 356716
Jun  7 01:59:27 ubuntu kernel: [ 1799.415735] Buffer I/O error on device sr0, logical block 356717
Jun  7 01:59:27 ubuntu kernel: [ 1799.637355] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:27 ubuntu kernel: [ 1799.637357] Buffer I/O error on device sr0, logical block 356716
Jun  7 01:59:27 ubuntu kernel: [ 1799.637360] Buffer I/O error on device sr0, logical block 356717
Jun  7 01:59:28 ubuntu kernel: [ 1799.858856] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:28 ubuntu kernel: [ 1800.080482] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:28 ubuntu kernel: [ 1800.431356] end_request: I/O error, dev sr0, sector 1426864
Jun  7 01:59:28 ubuntu kernel: [ 1800.652856] end_request: I/O error, dev sr0, sector 1426864
```

---

### Post by infallible on 2009-06-07
just an update: i see that dmesg from the livecd session shows the same file system confusion.

---

### Post by infallible on 2009-06-09
I'm sure I'm violating etiquette by pounding posts into my own thread, so my apologies. I've scoured the forums here for solutions to a number of issues, and am always disappointed when I find relevant old threads with no further information...

I adjusted the OS-specific settings in my bios and removed the new PCI-E video card: Problem solved. There's some sort of I/O or ACPI conflict between the PCI-E bus and hard drive conrollers.

---

