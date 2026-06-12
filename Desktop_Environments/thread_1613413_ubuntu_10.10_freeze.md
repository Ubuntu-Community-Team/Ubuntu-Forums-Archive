---
title: "ubuntu 10.10 freeze"
date: 2010-11-04
forum: Desktop Environments
---

### Post by bsgz13z on 2010-11-04
Hi I am running Ubuntu on a desktop Pentium 4 3.00 Ghz, 1.5 GB ram, Nvidia 9500gt
I have installed the Video driver from Ubuntu s repository, But my cpu usage shoots up to 100% when ever i use firefox
and scroll web pages. Most of the time it freezes, keyboard and mouse have no response.
I had the same issues with other versions of Ubuntu as well :(

When running ubuntu 8.04 I found this in some forum for disabling cool n quiet option in bios

Open a Termina, then
1.
sudo su
cp /etc/init.d/powernowd /etc/init.d/powernowd.bak
gedit /etc/init.d/powernowd

2. Just after the line
#! /bin/sh
insert the following:
exit 0

3. Save the file and restart.

this actually seemed to work, I didnt have any crashes. when i upgrade to newer versions i was not able to find the powernowd package. I even tried doing the above after installin powernowd but it didnt work

---

### Post by azertyh on 2010-11-04
hello,

look at syslog to see some info :

```
tail -f /var/log/syslog
```CTRL+C to stop

or

```
dmesg
```very often, you can see in these files what is the cause.

---

### Post by bsgz13z on 2010-11-04
hi here s the output of dmesg


> [PHP]
[    0.182598] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
[    0.182653] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.182759] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.182767] pci 0000:00:02.0: PME# disabled
[    0.182870] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.182884] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.182897] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.182910] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.182923] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.182937] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f1ff]
[    0.182951] pci 0000:00:11.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.182999] pci 0000:00:11.0: supports D1 D2
[    0.183067] pci 0000:00:12.0: reg 10: [io  0xfa00-0xfa07]
[    0.183080] pci 0000:00:12.0: reg 14: [io  0xf900-0xf903]
[    0.183094] pci 0000:00:12.0: reg 18: [io  0xf800-0xf807]
[    0.183107] pci 0000:00:12.0: reg 1c: [io  0xf700-0xf703]
[    0.183121] pci 0000:00:12.0: reg 20: [io  0xf600-0xf60f]
[    0.183139] pci 0000:00:12.0: reg 24: [mem 0xfe02e000-0xfe02e1ff]
[    0.183157] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.183205] pci 0000:00:12.0: supports D1 D2
[    0.183266] pci 0000:00:13.0: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.183411] pci 0000:00:13.1: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.183567] pci 0000:00:13.2: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    0.183671] pci 0000:00:13.2: supports D1 D2
[    0.183676] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.183685] pci 0000:00:13.2: PME# disabled
[    0.183742] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.183756] pci 0000:00:14.0: reg 14: [mem 0xfe02a000-0xfe02a3ff]
[    0.183808] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.183865] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.183878] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.183892] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.183905] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.183918] pci 0000:00:14.1: reg 20: [io  0xf400-0xf40f]
[    0.184054] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.184152] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.184167] pci 0000:00:14.2: PME# disabled
[    0.184458] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.184475] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.184492] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.184503] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.184514] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.192032] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.192044] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.192051] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.192061] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.192152] pci 0000:02:02.0: reg 10: [io  0xde00-0xdeff]
[    0.192168] pci 0000:02:02.0: reg 14: [mem 0xfddff000-0xfddff0ff]
[    0.192280] pci 0000:02:02.0: supports D1 D2
[    0.192288] pci 0000:02:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.192298] pci 0000:02:02.0: PME# disabled
[    0.192391] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
[    0.192406] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.192416] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.192426] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.192431] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.192437] pci 0000:00:14.4:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.192458] pci_bus 0000:00: on NUMA node 0
[    0.192472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.211919] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212341] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212752] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212948] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11)
[    0.213138] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11)
[    0.213345] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[    0.213429] HEST: Table is not found!
[    0.213596] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.213603] vgaarb: loaded
[    0.213955] SCSI subsystem initialized
[    0.214130] libata version 3.00 loaded.
[    0.214239] usbcore: registered new interface driver usbfs
[    0.214267] usbcore: registered new interface driver hub
[    0.214321] usbcore: registered new device driver usb
[    0.214619] ACPI: WMI: Mapper loaded
[    0.214624] PCI: Using ACPI for IRQ routing
[    0.214630] PCI: pci_cache_line_size set to 64 bytes
[    0.214648] pci 0000:00:00.0: address space collision: [mem 0xe0000000-0xffffffff 64bit] conflicts with PCI Bus 0000:01 [mem 0xf8000000-0xfbffffff]
[    0.214762] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.214769] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.214774] reserve RAM buffer: 000000005fef0000 - 000000005fffffff 
[    0.214999] NetLabel: Initializing
[    0.215003] NetLabel:  domain hash size = 128
[    0.215007] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.215031] NetLabel:  unlabeled traffic allowed by default
[    0.215115] Switching to clocksource tsc
[    0.234231] AppArmor: AppArmor Filesystem Enabled
[    0.234262] pnp: PnP ACPI init
[    0.234302] ACPI: bus type pnp registered
[    0.235461] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.235481] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:00:11.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.235496] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:00:12.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.235533] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.239916] pnp 00:0d: disabling [mem 0x000d0000-0x000d3fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.239925] pnp 00:0d: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.239934] pnp 00:0d: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.239942] pnp 00:0d: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.239950] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.239959] pnp 00:0d: disabling [mem 0x00100000-0x5feeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.240082] pnp: PnP ACPI: found 14 devices
[    0.240087] ACPI: ACPI bus type pnp unregistered
[    0.240099] PnPBIOS: Disabled by ACPI PNP
[    0.240142] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.240150] system 00:01: [io  0x040b] has been reserved
[    0.240158] system 00:01: [io  0x04d6] has been reserved
[    0.240164] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.240170] system 00:01: [io  0x0c14] has been reserved
[    0.240175] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.240181] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.240186] system 00:01: [io  0x0c6f] has been reserved
[    0.240191] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.240197] system 00:01: [io  0x4000-0x40fe] has been reserved
[    0.240203] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.240210] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.240226] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.240232] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.240237] system 00:06: [io  0x0880-0x088f] has been reserved
[    0.240253] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.240267] system 00:0d: [mem 0x5ff00000-0x5fffffff] could not be reserved
[    0.240273] system 00:0d: [mem 0x5fef0000-0x5fefffff] could not be reserved
[    0.240279] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
[    0.240286] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.240292] system 00:0d: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.240298] system 00:0d: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.278345] pci 0000:00:11.0: BAR 6: assigned [mem 0x60000000-0x6007ffff pref]
[    0.278354] pci 0000:00:12.0: BAR 6: assigned [mem 0x60080000-0x600fffff pref]
[    0.278362] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb07ffff pref]
[    0.278367] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.278373] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.278381] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.278389] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.278398] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.278405] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.278419] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.278432] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.278461] pci 0000:00:02.0: setting latency timer to 64
[    0.278493] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.278498] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.278505] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.278510] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.278516] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.278521] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.278526] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.278531] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.278536] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.278541] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.278618] NET: Registered protocol family 2
[    0.278761] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.279299] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.280249] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.280849] TCP: Hash tables configured (established 131072 bind 65536)
[    0.280854] TCP reno registered
[    0.280860] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.280883] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.281092] NET: Registered protocol family 1
[    0.281118] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.356715] pci 0000:01:00.0: Boot video device
[    0.356730] PCI: CLS 32 bytes, default 64
[    0.357089] cpufreq-nforce2: No nForce2 chipset.
[    0.357162] Scanning for low memory corruption every 60 seconds
[    0.357427] audit: initializing netlink socket (disabled)
[    0.357449] type=2000 audit(1288941583.356:1): initialized
[    0.371483] highmem bounce pool size: 64 pages
[    0.371496] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.374620] VFS: Disk quotas dquot_6.5.2
[    0.374753] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.376073] fuse init (API version 7.14)
[    0.376261] msgmni has been set to 1696
[    0.377016] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.377027] io scheduler noop registered
[    0.377031] io scheduler deadline registered
[    0.377061] io scheduler cfq registered (default)
[    0.377249] pcieport 0000:00:02.0: setting latency timer to 64
[    0.377383] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.377430] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.377827] vesafb: framebuffer at 0xf9000000, mapped to 0xf8080000, using 768k, total 768k
[    0.377833] vesafb: mode is 1024x768x8, linelength=1024, pages=0
[    0.377837] vesafb: scrolling: redraw
[    0.377842] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    0.387287] Console: switching to colour frame buffer device 128x48
[    0.396568] fb0: VESA VGA frame buffer device
[    0.396838] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.396850] ACPI: Power Button [PWRB]
[    0.396960] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.396967] ACPI: Power Button [PWRF]
[    0.397081] ACPI: Fan [FAN] (on)
[    0.397398] ACPI: acpi_idle registered with cpuidle
[    0.406018] thermal LNXTHERM:01: registered as thermal_zone0
[    0.406035] ACPI: Thermal Zone [THRM] (40 C)
[    0.406142] ERST: Table is not found!
[    0.406491] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.406667] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.407349] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.410037] brd: module loaded
[    0.411247] loop: module loaded
[    0.411699]   alloc irq_desc for 23 on node -1
[    0.411704]   alloc kstat_irqs on node -1
[    0.411719] pata_acpi 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.411819]   alloc irq_desc for 22 on node -1
[    0.411824]   alloc kstat_irqs on node -1
[    0.411833] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.411893]   alloc irq_desc for 16 on node -1
[    0.411898]   alloc kstat_irqs on node -1
[    0.411906] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.412620] Fixed MDIO Bus: probed
[    0.412706] PPP generic driver version 2.4.2
[    0.412780] isapnp: Scanning for PnP cards...
[    0.462178] tun: Universal TUN/TAP device driver, 1.6
[    0.462184] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.462407] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.462474]   alloc irq_desc for 19 on node -1
[    0.462479]   alloc kstat_irqs on node -1
[    0.462493] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.462529] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.462600] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.462697] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02b000
[    0.506458] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.506794] hub 1-0:1.0: USB hub found
[    0.506805] hub 1-0:1.0: 8 ports detected
[    0.506988] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.507034] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.507067] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.507164] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.507205] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02d000
[    0.598954] hub 2-0:1.0: USB hub found
[    0.598968] hub 2-0:1.0: 4 ports detected
[    0.599119] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.599151] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.599255] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.599289] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02c000
[    0.665181] hub 3-0:1.0: USB hub found
[    0.665196] hub 3-0:1.0: 4 ports detected
[    0.665334] uhci_hcd: USB Universal Host Controller Interface driver
[    0.665525] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.671543] Freeing initrd memory: 10508k freed
[    0.685668] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.685689] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.685982] mice: PS/2 mouse device common for all mice
[    0.686214] rtc_cmos 00:03: RTC can wake from S4
[    0.686294] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.686331] rtc0: alarms up to one month, 242 bytes nvram
[    0.686558] device-mapper: uevent: version 1.0.3
[    0.686780] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.686913] device-mapper: multipath: version 1.1.1 loaded
[    0.686918] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.687133] EISA: Probing bus 0 at eisa.0
[    0.687162] Cannot allocate resource for EISA slot 4
[    0.687188] EISA: Detected 0 cards.
[    0.687327] cpuidle: using governor ladder
[    0.687332] cpuidle: using governor menu
[    0.687944] TCP cubic registered
[    0.688198] NET: Registered protocol family 10
[    0.688970] lo: Disabled Privacy Extensions
[    0.689434] NET: Registered protocol family 17
[    0.690744] Using IPI No-Shortcut mode
[    0.690881] PM: Resume from disk failed.
[    0.690905] registered taskstats version 1
[    0.691261]   Magic number: 2:417:318
[    0.691311] tty tty43: hash matches
[    0.691399] rtc_cmos 00:03: setting system clock to 2010-11-05 07:19:44 UTC (1288941584)
[    0.691404] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.691408] EDD information not available.
[    0.704414] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.731085] isapnp: No Plug & Play device found
[    0.731124] Freeing unused kernel memory: 684k freed
[    0.732083] Write protecting the kernel text: 4932k
[    0.732140] Write protecting the kernel read-only data: 1976k
[    0.758242] udev[75]: starting version 163
[    0.944283] sata_sil 0000:00:11.0: version 2.4
[    0.947249] Floppy drive(s): fd0 is 1.44M
[    0.966837] scsi0 : sata_sil
[    0.974018] FDC 0 is a post-1991 82077
[    0.979398] scsi1 : sata_sil
[    0.979511] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    0.979520] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    0.980454] scsi2 : sata_sil
[    0.980641] scsi3 : sata_sil
[    0.980728] ata3: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 22
[    0.980736] ata4: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 22
[    0.981250] scsi4 : pata_atiixp
[    0.981444] scsi5 : pata_atiixp
[    0.983673] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    0.983679] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    0.984946] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.984975] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.157390] ata6.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.04, max UDMA/66
[    1.157425] ata6.00: limited to UDMA/33 due to 40-wire cable
[    1.173372] ata6.00: configured for UDMA/33
[    1.268058] ata1: SATA link down (SStatus 0 SControl 310)
[    1.268078] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.315646] ata3.00: ATA-7: ST3802110AS, 3.AAE, max UDMA/133
[    1.315651] ata3.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.382320] ata3.00: configured for UDMA/100
[    1.588034] ata2: SATA link down (SStatus 0 SControl 310)
[    1.588245] scsi 2:0:0:0: Direct-Access     ATA      ST3802110AS      3.AA PQ: 0 ANSI: 5
[    1.588556] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.588591] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.588813] sd 2:0:0:0: [sda] Write Protect is off
[    1.588818] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.588872] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.589167]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.669464] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.908035] ata4: SATA link down (SStatus 0 SControl 310)
[    1.909284] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 5
[    1.912938] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.912943] Uniform CD-ROM driver Revision: 3.20
[    1.913113] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.913224] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.926860] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.926941]   alloc irq_desc for 21 on node -1
[    1.926946]   alloc kstat_irqs on node -1
[    1.926999] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.929306] 8139too 0000:02:02.0: eth0: RealTek RTL8139 at 0xde00, 00:16:76:42:c6:0f, IRQ 21
[    3.096890] EXT4-fs (sda9): INFO: recovery required on readonly filesystem
[    3.096903] EXT4-fs (sda9): write access will be enabled during recovery
[    4.469601] EXT4-fs (sda9): orphan cleanup on readonly fs
[    4.480079] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 435403
[    4.480193] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 435402
[    4.480518] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 418273
[    4.480598] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 418225
[    4.480867] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 427847
[    4.480953] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 427845
[    4.480982] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547480
[    4.481011] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547479
[    4.481037] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547478
[    4.481063] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547477
[    4.481089] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547462
[    4.481117] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547476
[    4.481143] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547475
[    4.481169] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547474
[    4.481194] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547473
[    4.481220] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547472
[    4.481246] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547471
[    4.481272] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547470
[    4.481297] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547469
[    4.481323] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547468
[    4.481349] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547467
[    4.481375] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547466
[    4.481400] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547465
[    4.481426] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547464
[    4.481452] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547463
[    4.481478] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 547318
[    4.481563] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 417053
[    4.481620] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 170900
[    4.481638] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 417094
[    4.481667] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 412497
[    4.481696] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 134856
[    4.481715] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 170747
[    4.481743] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 170564
[    4.481771] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 170526
[    4.481798] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 131764
[    4.481825] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 131763
[    4.481851] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 131757
[    4.481878] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 133237
[    4.481918] EXT4-fs (sda9): 38 orphan inodes deleted
[    4.481924] EXT4-fs (sda9): recovery complete
[    4.707703] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   20.471810] udev[302]: starting version 163
[   20.512115] Adding 554204k swap on /dev/sda8.  Priority:-1 extents:1 across:554204k 
[   20.649072] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SM00 [??? 0x00000b00-0x00000b07 flags 0x30]
[   20.649081] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.857653] lp: driver loaded but no devices found
[   20.895064] Linux agpgart interface v0.103
[   20.974254] psmouse serio1: ID: 10 00 64
[   20.988267] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   20.990100] parport_pc 00:09: reported by Plug and Play ACPI
[   20.990188] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.036553] logips2pp: Detected unknown logitech mouse model 106
[   21.062422] ppdev: user-space parallel port driver
[   21.092380] lp0: using parport0 (interrupt-driven).
[   21.104437] type=1400 audit(1288921804.907:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=526 comm="apparmor_parser"
[   21.105328] type=1400 audit(1288921804.911:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
[   21.105831] type=1400 audit(1288921804.911:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
[   21.364850] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.455276] type=1400 audit(1288921805.259:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=697 comm="apparmor_parser"
[   21.458681] type=1400 audit(1288921805.263:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=698 comm="apparmor_parser"
[   21.459572] type=1400 audit(1288921805.263:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=698 comm="apparmor_parser"
[   21.460069] type=1400 audit(1288921805.263:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=698 comm="apparmor_parser"
[   21.482550] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   21.488409] type=1400 audit(1288921805.291:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=699 comm="apparmor_parser"
[   21.491562] type=1400 audit(1288921805.295:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=701 comm="apparmor_parser"
[   21.492653] type=1400 audit(1288921805.299:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=701 comm="apparmor_parser"
[   21.580581] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[   21.614070] nvidia: module license 'NVIDIA' taints kernel.
[   21.614077] Disabling lock debugging due to kernel taint
[   22.975328]   alloc irq_desc for 18 on node -1
[   22.975335]   alloc kstat_irqs on node -1
[   22.975349] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.975364] nvidia 0000:01:00.0: setting latency timer to 64
[   22.975374] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.977587] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   25.688949] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
[   31.620014] eth0: no IPv6 routers present
[   33.914947] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
[   61.349904] lo: Disabled Privacy Extensions[/PHP]

---

### Post by bsgz13z on 2010-11-04
and tail -f /var/log/syslog

[PHP]
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Successfully made thread 1337 of process 1337 (n/a) owned by '1000' high priority at nice level -11.
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Supervising 4 threads of 2 processes of 2 users.
Nov  5 07:20:22 girish-desktop x-session-manager[1263]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Successfully made thread 1345 of process 1337 (n/a) owned by '1000' RT at priority 5.
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Supervising 5 threads of 2 processes of 2 users.
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Successfully made thread 1348 of process 1337 (n/a) owned by '1000' RT at priority 5.
Nov  5 07:20:22 girish-desktop rtkit-daemon[1165]: Supervising 6 threads of 2 processes of 2 users.
Nov  5 07:20:45 girish-desktop kernel: [   61.349904] lo: Disabled Privacy Extensions
Nov  5 07:25:06 girish-desktop anacron[809]: Job `cron.daily' started
Nov  5 07:25:06 girish-desktop anacron[1563]: Updated timestamp for job `cron.daily' to 2010-11-05

[/PHP]

---

### Post by azertyh on 2010-11-05
> **bsgz13z said:**
> But my cpu usage shoots up to 100% when ever i use firefox and scroll web pages.
 
hello,
everytime i read web pages with full flash, i have more than 50% of the cpu usage.
but in a "simply" web pages like ubuntuforums, just 1%.

---

### Post by bsgz13z on 2010-11-05
its not just that my computer freezes randomly :(

---

### Post by chris0108 on 2010-11-05
I get a similar problem running xubuntu, when running a web browser with anything that is flash dependant it will crash but not all the time?? If you google (i know hard if you browser is crashing all the time!) flash for linux, you will find that its not as well made or supported as it is for windows, but HTML5 will sort it all out??

---

### Post by bsgz13z on 2010-11-05
Its not just with the browser system crashes even if i use others apps its just more frequent with browsers

---

### Post by chris0108 on 2010-11-05
I wonder if this is an intel pentium 4 problem, im running basically the same processor (pentium 4 2.4ghz) mine mainly seamed to freeze whilst web browsing, iv tried ubuntu, lubuntu, and now on xubuntu all run about the same. Strange thing is i have backtrack(ubuntu based) on a spare hard drive, it has problems booting but once running its just fine??

---

### Post by bsgz13z on 2010-11-06
I have no booting problem, random freeze for about every 20 min

---

### Post by azertyh on 2010-11-06
hello,
found this [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
do a search on [https://launchpad.net/](https://launchpad.net/) too. perhaps someone had the same problem and it was solved.

---

### Post by @lpha on 2010-11-06
Hello bsjz13z, I had the exact same problem that you had. The cool & quiet feature causes ubuntu to crash, apparently. Take a look at the last post on my article w/ the link below. Since you couldn't find the powernowd package (I couldn't find it either when I had the problem), maybe you should consider disabling it through the bios.


[http://ubuntuforums.org/showthread.php?t=1589135](http://ubuntuforums.org/showthread.php?t=1589135)

---

