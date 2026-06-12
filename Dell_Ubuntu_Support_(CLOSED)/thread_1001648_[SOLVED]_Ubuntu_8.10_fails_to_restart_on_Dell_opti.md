---
title: "[SOLVED] Ubuntu 8.10 fails to restart on Dell optiplex 330"
date: 2008-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by babloo75 on 2008-12-04
I am facing a very strange problem on my new desktop optiplex 330. [dual boot- ubuntu 8.10(gnome environment)with win xp] initially it used to be a problem with shutdown as well as restart, both.
but after following the advice in a forum, it is partially solved by method described below

by opening in terminal
sudo gedit /etc/init.d/alsa-utils

and then scrolling down to the stop line and adding
ifconfig eth0 down

it seems to be solved partially (partially because when i give a command to shutdown, it shuts down. but when i try to restart it fails to shut down and freezes at the end of orange bar becoming black-- and then it stays there indefinitely..
i have to switch off my computer manually with hard shut down. i m sure sure this is going to screw my computer's hardware..

can anybody suggest a remedy...
Thanks in advance.

---

### Post by andreasis on 2008-12-05
Hi,

As a first step I'd like to ask you to take a look at /var/log (accessible from System > Administration > System Log, and post any issues that you see,so that we know where to start.

---

### Post by babloo75 on 2008-12-06
Thanx for replying.
As asked by you, I opened System > Admin > System monitor
But I get  huge list of things and i m confused how to proceed further. any way i have attached a screen shot of the user log command.. is it ok to proceed further? I have just now changed my internet modem device also thinking that it might be conflicting with restart of ubuntu. but the problem persists (even if internet is on/off).

Thanks again..

---

### Post by andreasis on 2008-12-07
Hi, sorry for the delay.

I have a few ideas, but I want to cover just one more source that may identify a specific solution to the issue of ubuntu hanging when you restart, but shutting down when you tell it to shut down.  It's just so I don't go on my rant/list of things to try, when the problem could be right under out noses.

First, please restart the computer so the problem happens, and post the time at which you restarted.  Then, from the program in your screenshot, could you click on syslog on the left hand side, rather than the user log? An alternative would be to open the syslog in gedit by ```
gedit /var/log/syslog
```

Can you post the output of that file on here too?  There may just be an entry at/around the time of the restart that would indicate the reason as to why ubuntu fails to restart properly.

---

### Post by babloo75 on 2008-12-07
> **andreasis said:**
> Hi, sorry for the delay.

I have a few ideas, but I want to cover just one more source that may identify a specific solution to the issue of ubuntu hanging when you restart, but shutting down when you tell it to shut down.  It's just so I don't go on my rant/list of things to try, when the problem could be right under out noses.

First, please restart the computer so the problem happens, and post the time at which you restarted.  Then, from the program in your screenshot, could you click on syslog on the left hand side, rather than the user log? An alternative would be to open the syslog in gedit by ```
gedit /var/log/syslog
```

Can you post the output of that file on here too?  There may just be an entry at/around the time of the restart that would indicate the reason as to why ubuntu fails to restart properly.

Hi andreasis,
How r u. Thanks again for the reply. As asked by you, I did restart of my computer at about 18:49 HRS on Dec 7, and again started my computer. here are the screenshots of the syslog.

---

### Post by babloo75 on 2008-12-07
Sorry i tried to paste the long file here too, but it is failing to attach.
Will the above screen shots solve the purpose ?

---

### Post by babloo75 on 2008-12-07
Here is the output of same command in terminal. I restarted my computer at about 19:46 pm on Dec 7 and got the following result. (Sorry for any fault.. I m new to linux.. is gedit the same as terminal?)


Dec  7 19:18:32 babloo-desktop avahi-daemon[4456]: New relevant interface eth0.IPv4 for mDNS.
Dec  7 19:18:32 babloo-desktop avahi-daemon[4456]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Dec  7 19:18:32 babloo-desktop dhclient: bound to 192.168.1.2 -- renewal in 1738 seconds.
Dec  7 19:18:33 babloo-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec  7 19:30:49 babloo-desktop -- MARK --
Dec  7 19:46:42 babloo-desktop kernel: [ 3366.010794] compiz.real[5267]: segfault at 656477 ip 08055c7d sp bfaed8f0 error 4 in compiz.real[8048000+34000]
Dec  7 19:46:42 babloo-desktop init: tty4 main process (4047) killed by TERM signal
Dec  7 19:46:42 babloo-desktop init: tty5 main process (4048) killed by TERM signal
Dec  7 19:46:42 babloo-desktop init: tty2 main process (4055) killed by TERM signal
Dec  7 19:46:42 babloo-desktop init: tty3 main process (4056) killed by TERM signal
Dec  7 19:46:42 babloo-desktop init: tty6 main process (4057) killed by TERM signal
Dec  7 19:46:42 babloo-desktop init: tty1 main process (4989) killed by TERM signal
Dec  7 19:46:42 babloo-desktop kernel: [ 3366.487714] mtrr: no MTRR for c0000000,10000000 found
Dec  7 19:46:43 babloo-desktop kernel: [ 3367.372068] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec  7 19:46:43 babloo-desktop kernel: [ 3367.372073] apm: disabled on user request.
Dec  7 19:46:45 babloo-desktop kernel: [ 3369.314512] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec  7 19:46:46 babloo-desktop bluetoothd[4709]: bridge pan0 removed
Dec  7 19:46:46 babloo-desktop bluetoothd[4709]: Stopping SDP server
Dec  7 19:46:46 babloo-desktop bluetoothd[4709]: Exit
Dec  7 19:46:46 babloo-desktop avahi-daemon[4456]: Got SIGTERM, quitting.
Dec  7 19:46:46 babloo-desktop avahi-daemon[4456]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Dec  7 19:46:47 babloo-desktop exiting on signal 15
Dec  7 19:47:34 babloo-desktop syslogd 1.5.0#2ubuntu6: restart.
Dec  7 19:47:34 babloo-desktop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec  7 19:47:34 babloo-desktop kernel: Cannot find map file.
Dec  7 19:47:34 babloo-desktop kernel: Loaded 47838 symbols from 79 modules.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f55ac00 (usable)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 000000007f55ac00 - 000000007f55ec00 (ACPI NVS)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 000000007f55ec00 - 000000007f560c00 (ACPI data)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 000000007f560c00 - 0000000080000000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] last_pfn = 0x7f55a max_arch_pfn = 0x100000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] RAMDISK: 3781f000 - 37fefd9c
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] DMI 2.5 present.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: XSDT 000FD02D, 005C (r1 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: FACP 000FD14D, 00F4 (r3 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: DSDT FFF5DDDF, 332A (r1   DELL    dt_ex     1000 INTL 20050624)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: FACS 7F55AC00, 0040
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: SSDT FFF6122A, 00AC (r1   DELL    st_ex     1000 INTL 20050624)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: APIC 000FD241, 0092 (r1 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: BOOT 000FD2D3, 0028 (r1 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: ASF! 000FD2FB, 0092 (r32 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: MCFG 000FD38D, 003E (r1 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: HPET 000FD3CB, 0038 (r1 DELL    B9K           15 ASL        61)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] 1141MB HIGHMEM available.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] 896MB LOWMEM available.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   low ram: 00000000 - 38000000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #4 [003781f000 - 0037fefd9c]          RAMDISK ==> [003781f000 - 0037fefd9c]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] 000fe710
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Zone PFN ranges:
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f55a
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Movable zone start PFN for each node
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f55a
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] On node 0 totalpages: 521465
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000]   HighMem zone: 289617 pages, LIFO batch:31
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000f0000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 516880
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Kernel command line: root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro quiet splash 
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Initializing CPU#0
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] TSC: using PMTIMER calibration value
Dec  7 19:47:34 babloo-desktop kernel: [    0.000000] Detected 2526.973 MHz processor.
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] console [tty0] enabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Memory: 2052504k/2086248k available (2572k kernel code, 32456k reserved, 1160k data, 424k init, 1168744k highmem)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] virtual kernel memory layout:
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] hpet clockevent registered
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.94 BogoMIPS (lpj=10107892)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Security Framework initialized
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: Processor Core ID: 0
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] using mwait in idle threads.
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Dec  7 19:47:34 babloo-desktop kernel: [    0.017628] ACPI: Core revision 20080609
Dec  7 19:47:34 babloo-desktop kernel: [    0.063986] ACPI: Checking initramfs for custom DSDT
Dec  7 19:47:34 babloo-desktop kernel: [    0.398179] ENABLING IO-APIC IRQs
Dec  7 19:47:34 babloo-desktop kernel: [    0.398347] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  7 19:47:34 babloo-desktop kernel: [    0.438042] CPU0: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz stepping 06
Dec  7 19:47:34 babloo-desktop kernel: [    0.440027] Booting processor 1/1 ip 6000
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Initializing CPU#1
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5053.89 BogoMIPS (lpj=10107780)
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec  7 19:47:34 babloo-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Dec  7 19:47:34 babloo-desktop kernel: [    0.524552] CPU1: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz stepping 06
Dec  7 19:47:34 babloo-desktop kernel: [    0.524565] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec  7 19:47:34 babloo-desktop kernel: [    0.528048] Brought up 2 CPUs
Dec  7 19:47:34 babloo-desktop kernel: [    0.528050] Total of 2 processors activated (10107.83 BogoMIPS).
Dec  7 19:47:34 babloo-desktop kernel: [    0.528070] CPU0 attaching sched-domain:
Dec  7 19:47:34 babloo-desktop kernel: [    0.528072]  domain 0: span 0-1 level MC
Dec  7 19:47:34 babloo-desktop kernel: [    0.528074]   groups: 0 1
Dec  7 19:47:34 babloo-desktop kernel: [    0.528078] CPU1 attaching sched-domain:
Dec  7 19:47:34 babloo-desktop kernel: [    0.528080]  domain 0: span 0-1 level MC
Dec  7 19:47:34 babloo-desktop kernel: [    0.528082]   groups: 1 0
Dec  7 19:47:34 babloo-desktop kernel: [    0.528143] net_namespace: 840 bytes
Dec  7 19:47:34 babloo-desktop kernel: [    0.528143] Booting paravirtualized kernel on bare hardware
Dec  7 19:47:34 babloo-desktop kernel: [    0.528234] Time: 19:47:22  Date: 12/07/08
Dec  7 19:47:34 babloo-desktop kernel: [    0.528255] NET: Registered protocol family 16
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] EISA bus registered
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] ACPI: bus type pci registered
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] PCI: MCFG area at e0000000 reserved in E820
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] PCI: Using MMCONFIG for extended config space
Dec  7 19:47:34 babloo-desktop kernel: [    0.528270] PCI: Using configuration type 1 for base access
Dec  7 19:47:34 babloo-desktop kernel: [    0.528419] ACPI: EC: Look up EC in DSDT
Dec  7 19:47:34 babloo-desktop kernel: [    0.574025] ACPI: Interpreter enabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.574028] ACPI: (supports S0 S1 S3 S4 S5)
Dec  7 19:47:34 babloo-desktop kernel: [    0.574040] ACPI: Using IOAPIC for interrupt routing
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:01.0: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:02.0 reg 10 32bit mmio: [dfe00000, dfe7ffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:02.0 reg 14 io port: [ecd8, ecdf]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:02.0 reg 1c 32bit mmio: [dff00000, dfffffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:02.1 reg 10 32bit mmio: [dfe80000, dfefffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1b.0 reg 10 64bit mmio: [dfdfc000, dfdfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1b.0: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1c.0: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1d.0 reg 20 io port: [ff80, ff9f]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1d.1 reg 20 io port: [ff60, ff7f]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1d.2 reg 20 io port: [ff40, ff5f]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1d.3 reg 20 io port: [ff20, ff3f]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff980800, ff980bff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1d.7: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
Dec  7 19:47:34 babloo-desktop kernel: [    0.633518] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636047] PCI: 0000:00:1f.2 reg 10 io port: [fe00, fe07]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636052] PCI: 0000:00:1f.2 reg 14 io port: [fe10, fe13]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636057] PCI: 0000:00:1f.2 reg 18 io port: [fe20, fe27]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636061] PCI: 0000:00:1f.2 reg 1c io port: [fe30, fe33]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636066] PCI: 0000:00:1f.2 reg 20 io port: [fec0, fecf]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636071] PCI: 0000:00:1f.2 reg 24 32bit mmio: [ff970000, ff9703ff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636085] pci 0000:00:1f.2: PME# supported from D3hot
Dec  7 19:47:34 babloo-desktop kernel: [    0.636088] pci 0000:00:1f.2: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.636124] PCI: 0000:00:1f.3 reg 20 io port: [ece0, ecff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636174] PCI: bridge 0000:00:01.0 32bit mmio: [dfc00000, dfcfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636235] PCI: 0000:02:00.0 reg 10 64bit mmio: [dfbf0000, dfbfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636281] pci 0000:02:00.0: PME# supported from D3hot D3cold
Dec  7 19:47:34 babloo-desktop kernel: [    0.636285] pci 0000:02:00.0: PME# disabled
Dec  7 19:47:34 babloo-desktop kernel: [    0.636314] PCI: bridge 0000:00:1c.0 32bit mmio: [dfb00000, dfbfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636359] pci 0000:00:1e.0: transparent bridge
Dec  7 19:47:34 babloo-desktop kernel: [    0.636376] bus 00 -> node 0
Dec  7 19:47:34 babloo-desktop kernel: [    0.636381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  7 19:47:34 babloo-desktop kernel: [    0.636861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
Dec  7 19:47:34 babloo-desktop kernel: [    0.637298] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Dec  7 19:47:34 babloo-desktop kernel: [    0.637642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Dec  7 19:47:34 babloo-desktop kernel: [    1.270413] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.270413] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.270413] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.272201] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Dec  7 19:47:34 babloo-desktop kernel: [    1.272559] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.272918] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.273247] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.273628] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
Dec  7 19:47:34 babloo-desktop kernel: [    1.273717] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  7 19:47:34 babloo-desktop kernel: [    1.273717] pnp: PnP ACPI init
Dec  7 19:47:34 babloo-desktop kernel: [    1.273717] ACPI: bus type pnp registered
Dec  7 19:47:34 babloo-desktop kernel: [    1.280145] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
Dec  7 19:47:34 babloo-desktop kernel: [    1.280148] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
Dec  7 19:47:34 babloo-desktop kernel: [    1.298927] pnp: PnP ACPI: found 9 devices
Dec  7 19:47:34 babloo-desktop kernel: [    1.298927] ACPI: ACPI bus type pnp unregistered
Dec  7 19:47:34 babloo-desktop kernel: [    1.298927] PnPBIOS: Disabled by ACPI PNP
Dec  7 19:47:34 babloo-desktop kernel: [    1.298927] PCI: Using ACPI for IRQ routing
Dec  7 19:47:34 babloo-desktop kernel: [    1.304041] NET: Registered protocol family 8
Dec  7 19:47:34 babloo-desktop kernel: [    1.304044] NET: Registered protocol family 20
Dec  7 19:47:34 babloo-desktop kernel: [    1.304062] NetLabel: Initializing
Dec  7 19:47:34 babloo-desktop kernel: [    1.304062] NetLabel:  domain hash size = 128
Dec  7 19:47:34 babloo-desktop kernel: [    1.304062] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  7 19:47:34 babloo-desktop kernel: [    1.304072] NetLabel:  unlabeled traffic allowed by default
Dec  7 19:47:34 babloo-desktop kernel: [    1.304077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec  7 19:47:34 babloo-desktop kernel: [    1.304081] hpet0: 3 64-bit timers, 14318180 Hz
Dec  7 19:47:34 babloo-desktop kernel: [    1.306461] tracer: 772 pages allocated for 65536 entries of 48 bytes
Dec  7 19:47:34 babloo-desktop kernel: [    1.306463]    actual entries 65620
Dec  7 19:47:34 babloo-desktop kernel: [    1.306521] AppArmor: AppArmor Filesystem Enabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.306538] ACPI: RTC can wake from S4
Dec  7 19:47:34 babloo-desktop kernel: [    1.308039] Switched to high resolution mode on CPU 0
Dec  7 19:47:34 babloo-desktop kernel: [    1.308580] Switched to high resolution mode on CPU 1
Dec  7 19:47:34 babloo-desktop kernel: [    1.312025] system 00:01: ioport range 0xc00-0xc7f has been reserved
Dec  7 19:47:34 babloo-desktop kernel: [    1.346989] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec  7 19:47:34 babloo-desktop kernel: [    1.346992] pci 0000:00:01.0:   IO window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.346995] pci 0000:00:01.0:   MEM window: 0xdfc00000-0xdfcfffff
Dec  7 19:47:34 babloo-desktop kernel: [    1.346997] pci 0000:00:01.0:   PREFETCH window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347001] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Dec  7 19:47:34 babloo-desktop kernel: [    1.347002] pci 0000:00:1c.0:   IO window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347006] pci 0000:00:1c.0:   MEM window: 0xdfb00000-0xdfbfffff
Dec  7 19:47:34 babloo-desktop kernel: [    1.347009] pci 0000:00:1c.0:   PREFETCH window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347014] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Dec  7 19:47:34 babloo-desktop kernel: [    1.347016] pci 0000:00:1e.0:   IO window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347019] pci 0000:00:1e.0:   MEM window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347022] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec  7 19:47:34 babloo-desktop kernel: [    1.347032] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  7 19:47:34 babloo-desktop kernel: [    1.347036] pci 0000:00:01.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    1.347041] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  7 19:47:34 babloo-desktop kernel: [    1.347044] pci 0000:00:1c.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    1.347049] pci 0000:00:1e.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    1.347052] bus: 00 index 0 io port: [0, ffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347054] bus: 00 index 1 mmio: [0, ffffffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347056] bus: 01 index 0 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347057] bus: 01 index 1 mmio: [dfc00000, dfcfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347059] bus: 01 index 2 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347060] bus: 01 index 3 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347062] bus: 02 index 0 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347063] bus: 02 index 1 mmio: [dfb00000, dfbfffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347064] bus: 02 index 2 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347066] bus: 02 index 3 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347067] bus: 03 index 0 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347069] bus: 03 index 1 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347070] bus: 03 index 2 mmio: [0, 0]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347071] bus: 03 index 3 io port: [0, ffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347073] bus: 03 index 4 mmio: [0, ffffffff]
Dec  7 19:47:34 babloo-desktop kernel: [    1.347079] NET: Registered protocol family 2
Dec  7 19:47:34 babloo-desktop kernel: [    1.360071] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    1.360236] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    1.360491] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    1.360631] TCP: Hash tables configured (established 131072 bind 65536)
Dec  7 19:47:34 babloo-desktop kernel: [    1.360633] TCP reno registered
Dec  7 19:47:34 babloo-desktop kernel: [    1.368094] NET: Registered protocol family 1
Dec  7 19:47:34 babloo-desktop kernel: [    1.368173] checking if image is initramfs... it is
Dec  7 19:47:34 babloo-desktop kernel: [    1.910091] Freeing initrd memory: 8003k freed
Dec  7 19:47:34 babloo-desktop kernel: [    1.910237] Simple Boot Flag at 0x7a set to 0x1
Dec  7 19:47:34 babloo-desktop kernel: [    1.910990] audit: initializing netlink socket (disabled)
Dec  7 19:47:34 babloo-desktop kernel: [    1.911009] type=2000 audit(1228679242.908:1): initialized
Dec  7 19:47:34 babloo-desktop kernel: [    1.915747] highmem bounce pool size: 64 pages
Dec  7 19:47:34 babloo-desktop kernel: [    1.915752] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec  7 19:47:34 babloo-desktop kernel: [    1.917552] VFS: Disk quotas dquot_6.5.1
Dec  7 19:47:34 babloo-desktop kernel: [    1.917617] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  7 19:47:34 babloo-desktop kernel: [    1.917696] msgmni has been set to 1743
Dec  7 19:47:34 babloo-desktop kernel: [    1.917789] io scheduler noop registered
Dec  7 19:47:34 babloo-desktop kernel: [    1.917791] io scheduler anticipatory registered
Dec  7 19:47:34 babloo-desktop kernel: [    1.917793] io scheduler deadline registered
Dec  7 19:47:34 babloo-desktop kernel: [    1.917802] io scheduler cfq registered (default)
Dec  7 19:47:34 babloo-desktop kernel: [    1.917815] pci 0000:00:02.0: Boot video device
Dec  7 19:47:34 babloo-desktop kernel: [    1.917962] pcieport-driver 0000:00:01.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    1.917988] pcieport-driver 0000:00:01.0: found MSI capability
Dec  7 19:47:34 babloo-desktop kernel: [    1.918012] pci_express 0000:00:01.0:pcie00: allocate port service
Dec  7 19:47:34 babloo-desktop kernel: [    1.918042] pci_express 0000:00:01.0:pcie03: allocate port service
Dec  7 19:47:34 babloo-desktop kernel: [    1.918103] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    1.918130] pcieport-driver 0000:00:1c.0: found MSI capability
Dec  7 19:47:34 babloo-desktop kernel: [    1.918157] pci_express 0000:00:1c.0:pcie00: allocate port service
Dec  7 19:47:34 babloo-desktop kernel: [    1.918188] pci_express 0000:00:1c.0:pcie02: allocate port service
Dec  7 19:47:34 babloo-desktop kernel: [    1.918217] pci_express 0000:00:1c.0:pcie03: allocate port service
Dec  7 19:47:34 babloo-desktop kernel: [    1.918451] isapnp: Scanning for PnP cards...
Dec  7 19:47:34 babloo-desktop kernel: [    2.271152] isapnp: No Plug & Play device found
Dec  7 19:47:34 babloo-desktop kernel: [    2.296321] hpet_resources: 0xfed00000 is busy
Dec  7 19:47:34 babloo-desktop kernel: [    2.296404] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Dec  7 19:47:34 babloo-desktop kernel: [    2.296511] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  7 19:47:34 babloo-desktop kernel: [    2.297040] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  7 19:47:34 babloo-desktop kernel: [    2.298359] brd: module loaded
Dec  7 19:47:34 babloo-desktop kernel: [    2.298411] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec  7 19:47:34 babloo-desktop kernel: [    2.298539] PNP: No PS/2 controller found. Probing ports directly.
Dec  7 19:47:34 babloo-desktop kernel: [    2.301072] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  7 19:47:34 babloo-desktop kernel: [    2.301077] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  7 19:47:34 babloo-desktop kernel: [    2.301265] mice: PS/2 mouse device common for all mice
Dec  7 19:47:34 babloo-desktop kernel: [    2.301359] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Dec  7 19:47:34 babloo-desktop kernel: [    2.301378] rtc0: alarms up to one day, hpet irqs
Dec  7 19:47:34 babloo-desktop kernel: [    2.301469] EISA: Probing bus 0 at eisa.0
Dec  7 19:47:34 babloo-desktop kernel: [    2.301492] EISA: Detected 0 cards.
Dec  7 19:47:34 babloo-desktop kernel: [    2.301494] cpuidle: using governor ladder
Dec  7 19:47:34 babloo-desktop kernel: [    2.301496] cpuidle: using governor menu
Dec  7 19:47:34 babloo-desktop kernel: [    2.301883] TCP cubic registered
Dec  7 19:47:34 babloo-desktop kernel: [    2.301905] Using IPI No-Shortcut mode
Dec  7 19:47:34 babloo-desktop kernel: [    2.302032] registered taskstats version 1
Dec  7 19:47:34 babloo-desktop kernel: [    2.302134]   Magic number: 4:813:798
Dec  7 19:47:34 babloo-desktop kernel: [    2.302157] tty ptyr6: hash matches
Dec  7 19:47:34 babloo-desktop kernel: [    2.302190] rtc_cmos 00:05: setting system clock to 2008-12-07 19:47:23 UTC (1228679243)
Dec  7 19:47:34 babloo-desktop kernel: [    2.302193] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  7 19:47:34 babloo-desktop kernel: [    2.302194] EDD information not available.
Dec  7 19:47:34 babloo-desktop kernel: [    2.302349] Freeing unused kernel memory: 424k freed
Dec  7 19:47:34 babloo-desktop kernel: [    2.302378] Write protecting the kernel text: 2576k
Dec  7 19:47:34 babloo-desktop kernel: [    2.302398] Write protecting the kernel read-only data: 936k
Dec  7 19:47:34 babloo-desktop kernel: [    2.400084] fuse init (API version 7.9)
Dec  7 19:47:34 babloo-desktop kernel: [    2.448144] processor ACPI0007:00: registered as cooling_device0
Dec  7 19:47:34 babloo-desktop kernel: [    2.448194] processor ACPI0007:01: registered as cooling_device1
Dec  7 19:47:34 babloo-desktop kernel: [    2.635775] usbcore: registered new interface driver usbfs
Dec  7 19:47:34 babloo-desktop kernel: [    2.635792] usbcore: registered new interface driver hub
Dec  7 19:47:34 babloo-desktop kernel: [    2.635820] usbcore: registered new device driver usb
Dec  7 19:47:34 babloo-desktop kernel: [    2.637400] USB Universal Host Controller Interface driver v3.0
Dec  7 19:47:34 babloo-desktop kernel: [    2.637439] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec  7 19:47:34 babloo-desktop kernel: [    2.637446] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    2.637449] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec  7 19:47:34 babloo-desktop kernel: [    2.637479] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec  7 19:47:34 babloo-desktop kernel: [    2.637504] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
Dec  7 19:47:34 babloo-desktop kernel: [    2.637614] usb usb1: configuration #1 chosen from 1 choice
Dec  7 19:47:34 babloo-desktop kernel: [    2.637637] hub 1-0:1.0: USB hub found
Dec  7 19:47:34 babloo-desktop kernel: [    2.637641] hub 1-0:1.0: 2 ports detected
Dec  7 19:47:34 babloo-desktop kernel: [    2.673032] No dock devices found.
Dec  7 19:47:34 babloo-desktop kernel: [    2.691204] SCSI subsystem initialized
Dec  7 19:47:34 babloo-desktop kernel: [    2.711378] libata version 3.00 loaded.
Dec  7 19:47:34 babloo-desktop kernel: [    2.848210] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Dec  7 19:47:34 babloo-desktop kernel: [    2.848218] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    2.848221] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec  7 19:47:34 babloo-desktop kernel: [    2.848240] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec  7 19:47:34 babloo-desktop kernel: [    2.848267] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
Dec  7 19:47:34 babloo-desktop kernel: [    2.848338] usb usb2: configuration #1 chosen from 1 choice
Dec  7 19:47:34 babloo-desktop kernel: [    2.848358] hub 2-0:1.0: USB hub found
Dec  7 19:47:34 babloo-desktop kernel: [    2.848363] hub 2-0:1.0: 2 ports detected
Dec  7 19:47:34 babloo-desktop kernel: [    2.952206] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  7 19:47:34 babloo-desktop kernel: [    2.952214] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    2.952217] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec  7 19:47:34 babloo-desktop kernel: [    2.952241] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec  7 19:47:34 babloo-desktop kernel: [    2.952268] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Dec  7 19:47:34 babloo-desktop kernel: [    2.952335] usb usb3: configuration #1 chosen from 1 choice
Dec  7 19:47:34 babloo-desktop kernel: [    2.952356] hub 3-0:1.0: USB hub found
Dec  7 19:47:34 babloo-desktop kernel: [    2.952361] hub 3-0:1.0: 2 ports detected
Dec  7 19:47:34 babloo-desktop kernel: [    2.956018] usb 1-1: new low speed USB device using uhci_hcd and address 2
Dec  7 19:47:34 babloo-desktop kernel: [    3.056140] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec  7 19:47:34 babloo-desktop kernel: [    3.056145] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    3.056148] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec  7 19:47:34 babloo-desktop kernel: [    3.056166] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Dec  7 19:47:34 babloo-desktop kernel: [    3.056189] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
Dec  7 19:47:34 babloo-desktop kernel: [    3.056251] usb usb4: configuration #1 chosen from 1 choice
Dec  7 19:47:34 babloo-desktop kernel: [    3.056270] hub 4-0:1.0: USB hub found
Dec  7 19:47:34 babloo-desktop kernel: [    3.056275] hub 4-0:1.0: 2 ports detected
Dec  7 19:47:34 babloo-desktop kernel: [    3.129713] usb 1-1: configuration #1 chosen from 1 choice
Dec  7 19:47:34 babloo-desktop kernel: [    3.160204] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec  7 19:47:34 babloo-desktop kernel: [    3.160215] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec  7 19:47:34 babloo-desktop kernel: [    3.160217] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec  7 19:47:34 babloo-desktop kernel: [    3.160235] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Dec  7 19:47:34 babloo-desktop kernel: [    3.164135] ehci_hcd 0000:00:1d.7: debug port 1
Dec  7 19:47:34 babloo-desktop kernel: [    3.164141] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec  7 19:47:34 babloo-desktop kernel: [    3.164145] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xff980800
Dec  7 19:47:34 babloo-desktop kernel: [    3.244019] usb 1-2: new low speed USB device using uhci_hcd and address 3
Dec  7 19:47:34 babloo-desktop kernel: [    3.256013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

---

### Post by andreasis on 2008-12-08
I'm very sorry for the delay, but I will be back in about 18 hours and I will do my best to get to the bottom of this : ).  I hope it's not a pressing issue..

---

### Post by babloo75 on 2008-12-08
> **andreasis said:**
> I'm very sorry for the delay, but I will be back in about 18 hours and I will do my best to get to the bottom of this : ).  I hope it's not a pressing issue..

No problem dear, take ur own time. I can wait till then. Bye.

---

### Post by scotty581 on 2008-12-17
I was having this same problem and found a work around on a different forum.  Try this:

-	Appending reboot=b to the kernel line in /boot/grub/menu.lst resolves the reboot problem on Dell OptiPlex 330.
-	Append "reboot=b" to the line begin with "kernel" like this:

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=9a0731d6-de74-40f0-8d90-acc0bc9e2264 ro **reboot=b**
initrd /boot/initrd.img-2.6.24-18-generic
quiet

---

### Post by babloo75 on 2008-12-18
> **scotty581 said:**
> I was having this same problem and found a work around on a different forum.  Try this:

-	Appending reboot=b to the kernel line in /boot/grub/menu.lst resolves the reboot problem on Dell OptiPlex 330.
-	Append "reboot=b" to the line begin with "kernel" like this:

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=9a0731d6-de74-40f0-8d90-acc0bc9e2264 ro **reboot=b**
initrd /boot/initrd.img-2.6.24-18-generic
quiet

Thanks Scotty 581.
But I couldn't understand it. I am new to linux and don't know how to start the procedure u advised. This much I understood that it needs to be done in terminal command.
Please dear.. explain the step by step procedure for doing the same.
Thanks once again.
Bye

---

### Post by babloo75 on 2008-12-18
Please help me...
Can anybody tell me about how to proceed for the instructions explained by Scotty581 in post no.10 above. I have Ubuntu 8.10 and the instructions mention about 8.04 versions.
Thanks in advance...

---

### Post by babloo75 on 2008-12-21
> **scotty581 said:**
> I was having this same problem and found a work around on a different forum.  Try this:

-	Appending reboot=b to the kernel line in /boot/grub/menu.lst resolves the reboot problem on Dell OptiPlex 330.
-	Append "reboot=b" to the line begin with "kernel" like this:

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=9a0731d6-de74-40f0-8d90-acc0bc9e2264 ro **reboot=b**
initrd /boot/initrd.img-2.6.24-18-generic
quiet

OK now I found the thing u described above.. But which one to choose from the list below.. here is the list of lines mentioning similar data as described above.. (total of 5 "titles" and which one to choose from above 4 "titles"). I opened the menu.lst file and found these 5 "titles" in my /boot/grub/menu.lst. Please tell which one to choose... here are they:

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ec72e884-c59a-4237-930e-f63159c97079
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ec72e884-c59a-4237-930e-f63159c97079
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ec72e884-c59a-4237-930e-f63159c97079
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ec72e884-c59a-4237-930e-f63159c97079
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ec72e884-c59a-4237-930e-f63159c97079
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Please help...

---

### Post by babloo75 on 2008-12-22
At last this problem has been solved...
Thanks to all of the members of Ubuntu community who supported me in solving this problem and to my friend Saurabh, with whom I had long telephonic conversations to understand the post from Scotty581.
adding "root (hd0,7) and reboot=b" solved my problem
Thanks once again.
:guitar:\\:D/:lol:):P

---

### Post by M3Haku on 2009-02-11
> **babloo75 said:**
> At last this problem has been solved...
Thanks to all of the members of Ubuntu community who supported me in solving this problem and to my friend Saurabh, with whom I had long telephonic conversations to understand the post from Scotty581.
adding "root (hd0,7) and reboot=b" solved my problem
Thanks once again.
:guitar:\\:D/:lol:):P

Hi There, just wanted to add that by adding the "reboot=b" the system boot in verbose mode but if you add this command after, you get everything back to normal, ie.,

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid ec72e884-c59a-4237-930e-f63159c97079
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=ec72e884-c59a-4237-930e-f63159c97079 ro quiet splash reboot-b
initrd /boot/initrd.img-2.6.27-7-generic
quiet

Cheers

---

