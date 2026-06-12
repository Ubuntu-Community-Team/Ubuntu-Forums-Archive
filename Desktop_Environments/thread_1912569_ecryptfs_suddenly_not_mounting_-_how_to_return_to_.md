---
title: "ecryptfs suddenly not mounting - how to return to normal situation"
date: 2012-01-20
forum: Desktop Environments
---

### Post by juju43 on 2012-01-20
Hello,

This morning, when starting my netbook (ubuntu 11.04), I came across a brand new desktop ... after little check, I saw that there was a problem mounting my ecryptfs home folder.

I have some backup but not everything and if possible, I want to recover most current data.


```

$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda7 on /opt type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/julien/.Private on /home/julien type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=0f0c10b2d5b48db2)
gvfs-fuse-daemon on /home/foo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=foo)
/dev/sdb1 on /media/1BE1-D538 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
$ df -h
Sys. de fichiers            Taille  Uti. Disp. Uti% Monté sur
/dev/sda6              44G   31G   11G  75% /
none                  992M  280K  992M   1% /dev
none                 1001M  372K 1001M   1% /dev/shm
none                 1001M  280K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
/dev/sda1             184M  133M   42M  77% /boot
/dev/sda7             184G  140G   36G  80% /opt
/home/julien/.Private
                       44G   31G   11G  75% /home/julien
$ sudo ecryptfs-recover-private
[sudo] password for julien:
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/home/.ecryptfs/julien/.Private].
Try to recover this directory? [Y/n]:
INFO: Enter your LOGIN passphrase...
Passphrase:

```Here I did some copy and after unmount, I backup the whole /home/.ecryptfs dir

Later
```

# ecryptfs-recover-private /home/.ecryptfs/julien
INFO: Found [/home/.ecryptfs/julien].
Try to recover this directory? [Y/n]:

INFO: Could not find your wrapped passphrase file.
INFO: To recover this directory, you MUST have your original MOUNT passphrase.
INFO: When you first setup your encrypted private directory, you were told to record
INFO: your MOUNT passphrase.
INFO: It should be 32 characters long, consisting of [0-9] and [a-f].

Enter your MOUNT passphrase:
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.J2O60pd3/private].
root@netbook:~# ls /tmp/ecryptfs.J2O60pd3/
private
root@netbook:~# ls /tmp/ecryptfs.J2O60pd3/private/
root@netbook:~# ls /tmp/ecryptfs.J2O60pd3/private/
# ecryptfs-recover-private /media/WD1/backup-.ecryptfs-20120121/
INFO: Found [/media/WD1/backup-.ecryptfs-20120121/].
Try to recover this directory? [Y/n]:

INFO: Could not find your wrapped passphrase file.
INFO: To recover this directory, you MUST have your original MOUNT passphrase.
INFO: When you first setup your encrypted private directory, you were told to record
INFO: your MOUNT passphrase.
INFO: It should be 32 characters long, consisting of [0-9] and [a-f].

Enter your MOUNT passphrase:
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.vO4Sp0sX/private].
root@netbook:~# ls /tmp/ecryptfs.vO4Sp0sX/
private
root@netbook:~# ls /tmp/ecryptfs.vO4Sp0sX/private/
root@netbook:~#

```Now it fails to mount anything either from original location or backup ???!!!!

I moved /home/.ecryptfs/julien to /home/.ecryptfs/julien.old and start repopulate my home dir but not as easy and it seems when I copied some stuff from ecrypts mount point, I got some empty dirs.
Also, I don't know how but at some point, it seems the systems has mixed/mounted multiple things at same mount point because I have in ls /home/.ecryptfs/julien.old/.Private/ both ECRYPTFS_FNEK_ENCRYPTED.* files, file I copied from ecryptfs and basic desktop structure ....

Any help to return to a normal desktop ?
Especially why ecrypt-recover-private mount empty folder now ?


dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-13-generic (buildd@mercury) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #54~ppa1~loms~natty-Ubuntu SMP Tue Dec 20 11:45:53 UTC 2011 (Ubuntu 2.6.38-13.54~ppa1~loms~natty-generic 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. N230                       /N230                       , BIOS 00MA.M000.20100518.JIP 05/18/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f7de0] f7de0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35cf6000 - 36e73000
[    0.000000] ACPI: RSDP 000f7db0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f5b8d8d 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5bfc92 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5b9ff5 05BA9 (v01  INTEL BEARG31A 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f5c2fc0 00040
[    0.000000] ACPI: MCFG 7f5bfd86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7f5bfdc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7f5bfdfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5bfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f5bfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f5b9395 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b92ef 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8df9 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5b0
[    0.000000] On node 0 totalpages: 521533
[    0.000000] free_area_init_node: node 0, pgdat c17820c0, node_mem_map f4d06200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292022 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517457
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-13-generic root=UUID=af8d1d90-90a8-4078-855f-4a11f84395c0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10432640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5b0)
[    0.000000] Memory: 2031404k/2086592k available (5187k kernel code, 54728k reserved, 2533k data, 700k init, 1177288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178b000 - 0xc183a000   ( 700 kB)
[    0.000000]       .data : 0xc1510f81 - 0xc178a440   (2533 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1510f81   (5187 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.650 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.30 BogoMIPS (lpj=6650600)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.008023] Security Framework initialized
[    0.008058] AppArmor: AppArmor initialized
[    0.008063] Yama: becoming mindful.
[    0.008185] Mount-cache hash table entries: 512
[    0.008445] Initializing cgroup subsys ns
[    0.008454] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008461] Initializing cgroup subsys cpuacct
[    0.008473] Initializing cgroup subsys memory
[    0.008491] Initializing cgroup subsys devices
[    0.008497] Initializing cgroup subsys freezer
[    0.008503] Initializing cgroup subsys net_cls
[    0.008508] Initializing cgroup subsys blkio
[    0.008574] CPU: Physical Processor ID: 0
[    0.008579] CPU: Processor Core ID: 0
[    0.008585] mce: CPU supports 5 MCE banks
[    0.008600] CPU0: Thermal monitoring handled by SMI
[    0.008608] using mwait in idle threads.
[    0.012864] ACPI: Core revision 20110112
[    0.024034] ftrace: allocating 23641 entries in 47 pages
[    0.028102] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028518] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070715] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f3caa000 soft=f3cac000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.164043] Brought up 2 CPUs
[    0.164053] Total of 2 processors activated (22609.64 BogoMIPS).
[    0.164577] devtmpfs: initialized
[    0.168260] print_constraints: dummy: 
[    0.168302] Time: 11:33:37  Date: 01/21/12
[    0.168388] NET: Registered protocol family 16
[    0.168414] Trying to unpack rootfs image as initramfs...
[    0.168705] EISA bus registered
[    0.168730] ACPI: bus type pci registered
[    0.168939] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.168951] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.168957] PCI: Using MMCONFIG for extended config space
[    0.168963] PCI: Using configuration type 1 for base access
[    0.172225] bio: create slab <bio-0> at 0
[    0.175984] ACPI: EC: Look up EC in DSDT
[    0.189914] ACPI: SSDT 7f5b9d1e 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.190776] ACPI: Dynamic OEM Table Load:
[    0.190788] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.191342] ACPI: SSDT 7f5b95f4 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.192160] ACPI: Dynamic OEM Table Load:
[    0.192171] ACPI: SSDT   (null) 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.193055] ACPI: SSDT 7f5b9f21 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.193894] ACPI: Dynamic OEM Table Load:
[    0.193905] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.194249] ACPI: SSDT 7f5b9c99 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.195055] ACPI: Dynamic OEM Table Load:
[    0.195066] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.196852] ACPI: Interpreter enabled
[    0.196852] ACPI: (supports S0 S3 S4 S5)
[    0.196852] ACPI: Using IOAPIC for interrupt routing
[    0.212182] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.252481] ACPI: No dock devices found.
[    0.252492] HEST: Table not found.
[    0.252506] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.254932] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.254957] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c22e88), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.254986] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.255013] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.259455] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.259467] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.259478] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.259487] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.259496] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.259505] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.259515] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.259524] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.259561] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.259639] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.259662] pci 0000:00:02.0: reg 10: [mem 0xf0300000-0xf037ffff]
[    0.259676] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.259690] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.259705] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.259764] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.259783] pci 0000:00:02.1: reg 10: [mem 0xf0380000-0xf03fffff]
[    0.259930] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.259971] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.260113] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.260126] pci 0000:00:1b.0: PME# disabled
[    0.260173] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.260292] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.260303] pci 0000:00:1c.0: PME# disabled
[    0.260353] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.260471] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.260483] pci 0000:00:1c.1: PME# disabled
[    0.260529] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.260647] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.260659] pci 0000:00:1c.2: PME# disabled
[    0.260707] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.260830] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.260843] pci 0000:00:1c.3: PME# disabled
[    0.260897] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.260976] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.261040] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.261118] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.261181] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.261260] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.261322] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.261401] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.261478] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.261516] pci 0000:00:1d.7: reg 10: [mem 0xf0604000-0xf06043ff]
[    0.261643] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.261655] pci 0000:00:1d.7: PME# disabled
[    0.261702] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.261823] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.261944] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.262014] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.262051] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.262072] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.262093] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.262114] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.262135] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.262156] pci 0000:00:1f.2: reg 24: [mem 0xf0604400-0xf06047ff]
[    0.262218] pci 0000:00:1f.2: PME# supported from D3hot
[    0.262229] pci 0000:00:1f.2: PME# disabled
[    0.262262] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.262345] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.262560] pci 0000:05:00.0: [14e4:4727] type 0 class 0x000280
[    0.262609] pci 0000:05:00.0: reg 10: [mem 0xf0100000-0xf0103fff 64bit]
[    0.262773] pci 0000:05:00.0: supports D1 D2
[    0.262781] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.262794] pci 0000:05:00.0: PME# disabled
[    0.268111] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.268126] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.268140] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.268156] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.268253] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.268264] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.268277] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.268293] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.268555] pci 0000:09:00.0: [11ab:4354] type 0 class 0x000200
[    0.268766] pci 0000:09:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.268873] pci 0000:09:00.0: reg 18: [io  0x2000-0x20ff]
[    0.269525] pci 0000:09:00.0: supports D1 D2
[    0.269534] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.269565] pci 0000:09:00.0: PME# disabled
[    0.269890] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.269904] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.269917] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.269935] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.270026] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.270038] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0000] (disabled)
[    0.270050] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.270067] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.270184] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.270197] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.270210] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.270226] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.270237] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.270247] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.270257] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.270267] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.270277] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.270287] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.270297] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.270306] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.270356] pci_bus 0000:00: on NUMA node 0
[    0.270373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.270658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.270812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.270954] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.271098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.271240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.271710] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.271733] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c22e88), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.271773]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.271978] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.271999] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c22e88), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.285394] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.285579] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.285751] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.285920] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.286101] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.286284] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.286479] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.286664] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.286980] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.287012] vgaarb: loaded
[    0.287665] SCSI subsystem initialized
[    0.287858] libata version 3.00 loaded.
[    0.288047] usbcore: registered new interface driver usbfs
[    0.288091] usbcore: registered new interface driver hub
[    0.288206] usbcore: registered new device driver usb
[    0.288570] wmi: Mapper loaded
[    0.288579] PCI: Using ACPI for IRQ routing
[    0.288589] PCI: pci_cache_line_size set to 64 bytes
[    0.288816] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.288827] reserve RAM buffer: 000000007f5b0000 - 000000007fffffff 
[    0.289142] NetLabel: Initializing
[    0.289149] NetLabel:  domain hash size = 128
[    0.289154] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.289183] NetLabel:  unlabeled traffic allowed by default
[    0.289315] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.289329] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.289345] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.296191] Switching to clocksource hpet
[    0.299774] Switched to NOHz mode on CPU #0
[    0.299834] Switched to NOHz mode on CPU #1
[    0.318092] AppArmor: AppArmor Filesystem Enabled
[    0.318171] pnp: PnP ACPI init
[    0.318226] ACPI: bus type pnp registered
[    0.320422] pnp 00:00: [bus 00-3f]
[    0.320433] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.320442] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.320450] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.320459] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.320468] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.320476] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.320485] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.320493] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.320502] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.320510] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.320519] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.320527] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.320535] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.320544] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.320557] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.320566] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.320575] pnp 00:00: [mem 0x80000000-0xf7ffffff window]
[    0.320583] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.320591] pnp 00:00: [mem 0x00000000 window]
[    0.320599] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.320799] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.321503] pnp 00:01: [io  0x0010-0x001f]
[    0.321513] pnp 00:01: [io  0x0024-0x0025]
[    0.321521] pnp 00:01: [io  0x0028-0x0029]
[    0.321528] pnp 00:01: [io  0x002c-0x002d]
[    0.321535] pnp 00:01: [io  0x0030-0x0031]
[    0.321542] pnp 00:01: [io  0x0034-0x0035]
[    0.321550] pnp 00:01: [io  0x0038-0x0039]
[    0.321557] pnp 00:01: [io  0x003c-0x003d]
[    0.321564] pnp 00:01: [io  0x0072-0x0077]
[    0.321571] pnp 00:01: [io  0x0080]
[    0.321578] pnp 00:01: [io  0x0090-0x009f]
[    0.321585] pnp 00:01: [io  0x00a4-0x00a5]
[    0.321592] pnp 00:01: [io  0x00a8-0x00a9]
[    0.321600] pnp 00:01: [io  0x00ac-0x00ad]
[    0.321607] pnp 00:01: [io  0x00b0-0x00b5]
[    0.321614] pnp 00:01: [io  0x00b8-0x00b9]
[    0.321621] pnp 00:01: [io  0x00bc-0x00bd]
[    0.321629] pnp 00:01: [io  0x0800-0x080f]
[    0.321636] pnp 00:01: [io  0x1000-0x107f]
[    0.321643] pnp 00:01: [io  0x1180-0x11bf]
[    0.321651] pnp 00:01: [io  0x002e-0x002f]
[    0.321658] pnp 00:01: [io  0x04d0-0x04d1]
[    0.321665] pnp 00:01: [io  0xfe00]
[    0.321672] pnp 00:01: [io  0x164e-0x174c]
[    0.321680] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.321688] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.321696] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.321704] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.321961] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.321971] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.321981] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.321992] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.322002] system 00:01: [io  0xfe00] has been reserved
[    0.322012] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.322025] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322036] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.322047] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.322057] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.322071] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322113] pnp 00:02: [io  0x0000-0x000f]
[    0.322121] pnp 00:02: [io  0x0081-0x008f]
[    0.322128] pnp 00:02: [io  0x00c0-0x00df]
[    0.322137] pnp 00:02: [dma 4]
[    0.322243] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.322278] pnp 00:03: [io  0x00f0-0x00fe]
[    0.322302] pnp 00:03: [irq 13]
[    0.322413] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322530] pnp 00:04: [io  0x0070-0x0071]
[    0.322547] pnp 00:04: [irq 8]
[    0.322654] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.322688] pnp 00:05: [io  0x0061]
[    0.322790] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.322870] pnp 00:06: [io  0x0060]
[    0.322877] pnp 00:06: [io  0x0064]
[    0.322892] pnp 00:06: [irq 1]
[    0.323000] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323050] pnp 00:07: [irq 12]
[    0.323177] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.324126] pnp 00:08: [mem 0xff800000-0xffffffff]
[    0.324257] pnp 00:08: Plug and Play ACPI device, IDs INT0800 (active)
[    0.324771] pnp: PnP ACPI: found 9 devices
[    0.324779] ACPI: ACPI bus type pnp unregistered
[    0.324789] PnPBIOS: Disabled by ACPI PNP
[    0.387389] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.387408] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.387425] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.387442] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.387457] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80800000-0x809fffff]
[    0.387472] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.387488] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.387500] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.387512] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.387522] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.387532] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.387546] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.387559] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.387576] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.387586] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.387600] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff]
[    0.387612] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.387629] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.387639] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.387653] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.387665] pci 0000:00:1c.2:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.387681] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.387690] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.387704] pci 0000:00:1c.3:   bridge window [mem 0x80800000-0x809fffff]
[    0.387716] pci 0000:00:1c.3:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.387733] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.387740] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.387752] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.387762] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.387816] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.387830] pci 0000:00:1c.0: setting latency timer to 64
[    0.387847] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.387869] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.387884] pci 0000:00:1c.1: setting latency timer to 64
[    0.387912] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.387924] pci 0000:00:1c.2: setting latency timer to 64
[    0.387941] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.387963] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.387977] pci 0000:00:1c.3: setting latency timer to 64
[    0.387994] pci 0000:00:1e.0: setting latency timer to 64
[    0.388044] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.388053] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.388062] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.388071] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.388080] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.388089] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.388098] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.388107] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.388116] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.388125] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.388134] pci_bus 0000:05: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.388143] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.388152] pci_bus 0000:07: resource 1 [mem 0x80200000-0x803fffff]
[    0.388161] pci_bus 0000:07: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.388171] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.388179] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.388188] pci_bus 0000:09: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.388197] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.388206] pci_bus 0000:0b: resource 1 [mem 0x80800000-0x809fffff]
[    0.388215] pci_bus 0000:0b: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.388225] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.388234] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.388243] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.388251] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.388261] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.388270] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.388280] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.388289] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.388395] NET: Registered protocol family 2
[    0.388585] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.389231] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.390323] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.390890] TCP: Hash tables configured (established 131072 bind 65536)
[    0.390901] TCP reno registered
[    0.390914] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.390939] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.391206] NET: Registered protocol family 1
[    0.391252] pci 0000:00:02.0: Boot video device
[    0.391604] PCI: CLS 32 bytes, default 64
[    0.391662] Simple Boot Flag at 0x36 set to 0x1
[    0.392243] cpufreq-nforce2: No nForce2 chipset.
[    0.392673] audit: initializing netlink socket (disabled)
[    0.392699] type=2000 audit(1327145617.388:1): initialized
[    0.416660] highmem bounce pool size: 64 pages
[    0.416678] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.422882] VFS: Disk quotas dquot_6.5.2
[    0.423080] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.425519] fuse init (API version 7.16)
[    0.425860] msgmni has been set to 1668
[    0.426649] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.426748] io scheduler noop registered
[    0.426755] io scheduler deadline registered
[    0.426819] io scheduler cfq registered (default)
[    0.427126] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.427220] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.427372] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.427463] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.427611] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.427692] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.427836] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.427917] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.428195] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.428274] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.428467] intel_idle: MWAIT substates: 0x20220
[    0.428485] intel_idle: v0.4 model 0x1C
[    0.428490] intel_idle: lapic_timer_reliable_states 0x2
[    0.428508] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.428948] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.429349] ACPI: AC Adapter [ADP1] (on-line)
[    0.429802] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.430028] ACPI: Lid Switch [LID0]
[    0.430187] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.484074] ACPI: Power Button [PWRB]
[    0.484274] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.484289] ACPI: Sleep Button [SLPB]
[    0.484443] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.484455] ACPI: Power Button [PWRF]
[    0.484901] ACPI: acpi_idle yielding to intel_idle
[    0.497413] thermal LNXTHERM:00: registered as thermal_zone0
[    0.497425] ACPI: Thermal Zone [TZ00] (55 C)
[    0.497580] ERST: Table is not found!
[    0.497773] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.498471] isapnp: Scanning for PnP cards...
[    0.518922] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.518946] ACPI: Battery Slot [BAT1] (battery present)
[    1.146969] Freeing initrd memory: 17908k freed
[    2.331235] isapnp: No Plug & Play device found
[    2.372111] Linux agpgart interface v0.103
[    2.372288] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    2.372490] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    2.372741] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    2.372956] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.375980] brd: module loaded
[    2.377471] loop: module loaded
[    2.377691] i2c-core: driver [adp5520] using legacy suspend method
[    2.377697] i2c-core: driver [adp5520] using legacy resume method
[    2.378730] Fixed MDIO Bus: probed
[    2.378823] PPP generic driver version 2.4.2
[    2.378932] tun: Universal TUN/TAP device driver, 1.6
[    2.378938] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.379145] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.379210] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.379243] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.379251] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.379354] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.379468] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    2.379487] ehci_hcd 0000:00:1d.7: debug port 1
[    2.383372] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.383407] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    2.396056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.396373] hub 1-0:1.0: USB hub found
[    2.396385] hub 1-0:1.0: 8 ports detected
[    2.396562] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.396598] uhci_hcd: USB Universal Host Controller Interface driver
[    2.396673] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.396689] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.396696] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.396793] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.396888] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.397190] hub 2-0:1.0: USB hub found
[    2.397203] hub 2-0:1.0: 2 ports detected
[    2.397348] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.397363] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.397370] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.397463] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.397591] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.397882] hub 3-0:1.0: USB hub found
[    2.397893] hub 3-0:1.0: 2 ports detected
[    2.398037] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.398051] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.398058] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.398162] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.400135] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.400446] hub 4-0:1.0: USB hub found
[    2.400457] hub 4-0:1.0: 2 ports detected
[    2.400604] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.400618] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.400625] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.400723] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.400852] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.401168] hub 5-0:1.0: USB hub found
[    2.401179] hub 5-0:1.0: 2 ports detected
[    2.401427] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.408149] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.408167] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.408495] mousedev: PS/2 mouse device common for all mice
[    2.409111] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.409157] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.409383] device-mapper: uevent: version 1.0.3
[    2.409583] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.409754] device-mapper: multipath: version 1.2.0 loaded
[    2.409763] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.409965] EISA: Probing bus 0 at eisa.0
[    2.409971] EISA: Cannot allocate resource for mainboard
[    2.409976] Cannot allocate resource for EISA slot 1
[    2.409981] Cannot allocate resource for EISA slot 2
[    2.409986] Cannot allocate resource for EISA slot 3
[    2.409990] Cannot allocate resource for EISA slot 4
[    2.409995] Cannot allocate resource for EISA slot 5
[    2.410000] Cannot allocate resource for EISA slot 6
[    2.410004] Cannot allocate resource for EISA slot 7
[    2.410009] Cannot allocate resource for EISA slot 8
[    2.410013] EISA: Detected 0 cards.
[    2.410296] cpuidle: using governor ladder
[    2.410509] cpuidle: using governor menu
[    2.411140] TCP cubic registered
[    2.411501] NET: Registered protocol family 10
[    2.412778] NET: Registered protocol family 17
[    2.412828] Registering the dns_resolver key type
[    2.412899] Using IPI No-Shortcut mode
[    2.413157] PM: Hibernation image not present or could not be loaded.
[    2.413181] registered taskstats version 1
[    2.413775]   Magic number: 12:740:580
[    2.413921] rtc_cmos 00:04: setting system clock to 2012-01-21 11:33:40 UTC (1327145620)
[    2.413930] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.413934] EDD information not available.
[    2.414181] Freeing unused kernel memory: 700k freed
[    2.414622] Write protecting the kernel text: 5188k
[    2.414709] Write protecting the kernel read-only data: 2148k
[    2.445596] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.465363] <30>udev[67]: starting version 167
[    2.724815] sky2: driver version 1.28
[    2.724934] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.724994] sky2 0000:09:00.0: setting latency timer to 64
[    2.725133] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    2.725797] sky2 0000:09:00.0: irq 44 for MSI/MSI-X
[    2.752261] sky2 0000:09:00.0: eth0: addr 00:24:54:ac:de:5d
[    2.837548] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    2.857910] [drm] Initialized drm 1.1.0 20060810
[    2.867581] ahci 0000:00:1f.2: version 3.0
[    2.867616] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.867728] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    2.867878] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.867891] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    2.867905] ahci 0000:00:1f.2: setting latency timer to 64
[    2.872189] scsi0 : ahci
[    2.876072] scsi1 : ahci
[    2.888271] scsi2 : ahci
[    2.892127] scsi3 : ahci
[    2.892635] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 45
[    2.892648] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 45
[    2.892659] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 45
[    2.892670] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 45
[    2.957285] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.957297] i915 0000:00:02.0: setting latency timer to 64
[    3.007764] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    3.007777] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.007782] [drm] Driver supports precise vblank timestamp query.
[    3.216067] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.216111] ata4: SATA link down (SStatus 0 SControl 300)
[    3.216170] ata3: SATA link down (SStatus 0 SControl 300)
[    3.216218] ata2: SATA link down (SStatus 0 SControl 300)
[    3.218877] ata1.00: ATA-8: ST92503010AS, 0003SDM1, max UDMA/133
[    3.218886] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.220051] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    3.222162] ata1.00: configured for UDMA/133
[    3.222440] scsi 0:0:0:0: Direct-Access     ATA      ST92503010AS     0003 PQ: 0 ANSI: 5
[    3.222949] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.223249] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.223452] sd 0:0:0:0: [sda] Write Protect is off
[    3.223462] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.223551] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.266286]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.267469] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.302282] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.302669] [drm] initialized overlay support
[    3.749571] fbcon: inteldrmfb (fb0) is primary device
[    3.750584] Console: switching to colour frame buffer device 128x37
[    3.750635] fb0: inteldrmfb frame buffer device
[    3.750640] drm: registered panic notifier
[    3.751985] ACPI Warning: _BQC returned an invalid level (20110112/video-473)
[    3.752680] acpi device:04: registered as cooling_device2
[    3.752960] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.753119] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[    3.754033] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.379789] Btrfs loaded
[    4.579307] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   24.938324] Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
[   25.033000] <30>udev[320]: starting version 167
[   25.100322] lp: driver loaded but no devices found
[   25.269051] vboxdrv: Found 2 processor cores.
[   25.269564] vboxdrv: fAsync=0 offMin=0x1e0 offMax=0x1e3c
[   25.269752] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   25.269760] vboxdrv: Successfully loaded version 4.1.8 (interface 0x00190000).
[   25.321774] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   25.470169] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   25.577002] lib80211: common routines for IEEE802.11 drivers
[   25.577015] lib80211_crypt: registered algorithm 'NULL'
[   25.697172] wl: module license 'MIXED/Proprietary' taints kernel.
[   25.697183] Disabling lock debugging due to kernel taint
[   25.716227] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   25.939629] type=1400 audit(1327106044.020:2): apparmor="STATUS" operation="profile_load" name="/usr/sbin/avahi-daemon" pid=685 comm="apparmor_parser"
[   25.944201] type=1400 audit(1327106044.028:3): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=694 comm="apparmor_parser"
[   25.946334] type=1400 audit(1327106044.028:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=694 comm="apparmor_parser"
[   25.947019] type=1400 audit(1327106044.028:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=694 comm="apparmor_parser"
[   26.533190] sky2 0000:09:00.0: eth0: enabling interface
[   26.550300] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.626796] wl 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.626821] wl 0000:05:00.0: setting latency timer to 64
[   26.933787] lib80211_crypt: registered algorithm 'TKIP'
[   27.081591] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   27.359304] type=1400 audit(1327106045.440:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1197 comm="apparmor_parser"
[   27.361272] type=1400 audit(1327106045.444:7): apparmor="STATUS" operation="profile_load" name="/bin/ping" pid=1196 comm="apparmor_parser"
[   27.404665] type=1400 audit(1327106045.488:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1203 comm="apparmor_parser"
[   27.409165] type=1400 audit(1327106045.492:9): apparmor="STATUS" operation="profile_load" name="/sbin/klogd" pid=1204 comm="apparmor_parser"
[   27.413431] type=1400 audit(1327106045.496:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1203 comm="apparmor_parser"
[   27.414163] type=1400 audit(1327106045.496:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1203 comm="apparmor_parser"
[   27.461771] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0400
[   27.513460] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   28.037472] Linux video capture interface: v2.00
[   28.158883] uvcvideo: Found UVC 1.00 device WebCam SCB-0370N (2232:1001)
[   28.163808] input: WebCam SCB-0370N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7
[   28.172357] usbcore: registered new interface driver uvcvideo
[   28.172368] USB Video Class driver (v1.0.0)
[   28.352510] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.352708] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   28.352811] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.554824] hda_codec: ALC269VB: BIOS auto-probing.
[   28.580752] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   28.604754] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   29.744364] ppdev: user-space parallel port driver
[   32.528626] vboxpci: IOMMU not found (not registered)
[   34.870465] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   34.880483] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   34.901477] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   38.192053] eth1: no IPv6 routers present
[  482.032100] CE: hpet increased min_delta_ns to 20113 nsec
[ 1004.461153] Intel AES-NI instructions are not detected.
[ 1004.481927] padlock_aes: VIA PadLock not detected.
[ 1040.188174] usb 1-7: new high speed USB device using ehci_hcd and address 4
[ 1040.952739] usbcore: registered new interface driver uas
[ 1040.971569] Initializing USB Mass Storage driver...
[ 1040.972539] scsi4 : usb-storage 1-7:1.0
[ 1040.974327] usbcore: registered new interface driver usb-storage
[ 1040.974337] USB Mass Storage support registered.
[ 1042.965547] scsi 4:0:0:0: Direct-Access     WD       My Passport 0730 1015 PQ: 0 ANSI: 6
[ 1042.966495] scsi 4:0:0:1: Enclosure         WD       SES Device       1015 PQ: 0 ANSI: 6
[ 1042.970081] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 1042.971682] scsi 4:0:0:1: Attached scsi generic sg2 type 13
[ 1047.200988] sd 4:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1047.201590] sd 4:0:0:0: [sdb] Write Protect is off
[ 1047.201605] sd 4:0:0:0: [sdb] Mode Sense: 47 00 10 08
[ 1047.201615] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1047.203619] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1047.217629]  sdb: sdb1 sdb2 sdb3
[ 1047.220461] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1047.220477] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1047.239379] ses 4:0:0:1: Attached Enclosure device
[ 1062.467971] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[ 1062.475033] EXT4-fs (sdb1): recovery complete
[ 1062.475839] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[ 1481.120240] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 1481.255118] scsi5 : usb-storage 1-3:1.0
[ 1482.257237] scsi 5:0:0:0: Direct-Access     SanDisk  U3 Titanium      4.06 PQ: 0 ANSI: 2
[ 1482.257823] scsi 5:0:0:1: CD-ROM            SanDisk  U3 Titanium      4.06 PQ: 0 ANSI: 2
[ 1482.261262] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1482.265415] sd 5:0:0:0: [sdc] 15695872 512-byte logical blocks: (8.03 GB/7.48 GiB)
[ 1482.267804] sd 5:0:0:0: [sdc] Write Protect is off
[ 1482.267825] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1482.267840] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1482.271188] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1482.271205] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 1482.271985] sr 5:0:0:1: Attached scsi CD-ROM sr0
[ 1482.272803] sr 5:0:0:1: Attached scsi generic sg4 type 5
[ 1482.273930] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1482.275774]  sdc: sdc1
[ 1482.279924] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1482.279941] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 1814.316609] show_signal_msg: 120 callbacks suppressed
[ 1814.316627] alarm-clock-app[6435]: segfault at 200 ip 00b30d6e sp bf86950c error 4 in libc-2.13.so[af1000+15a000]
```

---

