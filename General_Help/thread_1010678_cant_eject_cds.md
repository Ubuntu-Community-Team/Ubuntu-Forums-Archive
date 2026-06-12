---
title: "cant eject cds"
date: 2008-12-14
forum: General Help
---

### Post by grimey44 on 2008-12-14
hey, im new to ubuntu and am having multiple problems i cant seem to fix.
if anyone can help me that would be great.

i put a burned cdr into the my disc drive and when i try and copy songs off it, it starts copying then the progress on it stalls and just sits there. then after a while i press cancel it stops, then after this i am unable to physically eject the disk from my drive until i reset the computer.

anyone have similar problems?

---

### Post by Keen101 on 2008-12-14
you can alway's try typing in ```
eject
``` in a terminal.

---

### Post by lordbux on 2008-12-14
wow ...sounds complicated 
i will help so will lot of people

and don't restart your computer 
press Ctr + Alt + BakSpace instead 

it will take you to the log in screen log in back 
and open terminal and enter to open cdrom
   ```
eject 
``` 


and  about the copy problem 
pleas give the following detail
 
****your ram - memory capacity  
****out put for this command ```
lspci
```
****
and also try to copy using the terminal 


waiting for good news 
:KS

---

### Post by 3rdalbum on 2008-12-14
It sounds like your disc or possibly your drive is faulty. Although CD-Rs supposedly have a 50 year lifetime, in reality they can start losing data very quickly. It depends on the composition of the disc - I made a backup onto some blue TDK discs in 2005 and now they are unreadable. The very first music CD I burnt back in 1999 is still readable.

If you have the CD in and the program that's reading the disc seems to freeze, go into a terminal and type "dmesg". If the last lines are something like "Error reading sector 515567 on /dev/scd0", then Linux is encountering a problem in reading the disc.

---

### Post by DeMus on 2008-12-14
> **grimey44 said:**
> hey, im new to ubuntu and am having multiple problems i cant seem to fix.
if anyone can help me that would be great.

i put a burned cdr into the my disc drive and when i try and copy songs off it, it starts copying then the progress on it stalls and just sits there. then after a while i press cancel it stops, then after this i am unable to physically eject the disk from my drive until i reset the computer.

anyone have similar problems?

1) Go to Menu Places and click for example on Home Folder.
2) In the left column of the new window you also see your CD drive
3) Right click on it and choose unmount
4) Now it should be possible to open the drive door.

Good luck,
DeMus

---

### Post by grimey44 on 2008-12-14
so my ram  is 1024 MB
and i have a 160 GB hardrive

when i type the "lapci" command i get:

```
bash: lapci: command not found

```

and when it freezes while attempting to copy from the disk, 
when i type in "dmesg" i get this:
```
rved
[    0.788036] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.788040] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.788043] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.788046] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.788062] system 00:06: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.788071] system 00:08: ioport range 0x680-0x69f has been reserved
[    0.788074] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.788077] system 00:08: ioport range 0x1000-0x107f has been reserved
[    0.788080] system 00:08: ioport range 0x1180-0x11bf has been reserved
[    0.788084] system 00:08: ioport range 0xfe00-0xfe00 has been reserved
[    0.793334] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.793339] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.793347] pci 0000:00:1c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.793353] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.793362] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:05
[    0.793367] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.793374] pci 0000:00:1c.1:   MEM window: 0xf4200000-0xf42fffff
[    0.793379] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.793389] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.793391] pci 0000:00:1c.2:   IO window: disabled
[    0.793398] pci 0000:00:1c.2:   MEM window: disabled
[    0.793403] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.793412] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
[    0.793414] pci 0000:00:1c.3:   IO window: disabled
[    0.793422] pci 0000:00:1c.3:   MEM window: 0xf4300000-0xf43fffff
[    0.793427] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.793436] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.793439] pci 0000:00:1e.0:   IO window: disabled
[    0.793446] pci 0000:00:1e.0:   MEM window: 0xf4400000-0xf44fffff
[    0.793451] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.793475] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.793482] pci 0000:00:1c.0: setting latency timer to 64
[    0.793493] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.793500] pci 0000:00:1c.1: setting latency timer to 64
[    0.793511] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.793517] pci 0000:00:1c.2: setting latency timer to 64
[    0.793528] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.793534] pci 0000:00:1c.3: setting latency timer to 64
[    0.793544] pci 0000:00:1e.0: setting latency timer to 64
[    0.793549] bus: 00 index 0 io port: [0, ffff]
[    0.793551] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.793554] bus: 02 index 0 io port: [2000, 2fff]
[    0.793556] bus: 02 index 1 mmio: [f2000000, f3ffffff]
[    0.793558] bus: 02 index 2 mmio: [f0000000, f1ffffff]
[    0.793560] bus: 02 index 3 mmio: [0, 0]
[    0.793563] bus: 05 index 0 io port: [3000, 3fff]
[    0.793565] bus: 05 index 1 mmio: [f4200000, f42fffff]
[    0.793567] bus: 05 index 2 mmio: [0, 0]
[    0.793569] bus: 05 index 3 mmio: [0, 0]
[    0.793571] bus: 06 index 0 mmio: [0, 0]
[    0.793573] bus: 06 index 1 mmio: [0, 0]
[    0.793575] bus: 06 index 2 mmio: [0, 0]
[    0.793576] bus: 06 index 3 mmio: [0, 0]
[    0.793578] bus: 07 index 0 mmio: [0, 0]
[    0.793580] bus: 07 index 1 mmio: [f4300000, f43fffff]
[    0.793583] bus: 07 index 2 mmio: [0, 0]
[    0.793584] bus: 07 index 3 mmio: [0, 0]
[    0.793587] bus: 08 index 0 mmio: [0, 0]
[    0.793589] bus: 08 index 1 mmio: [f4400000, f44fffff]
[    0.793591] bus: 08 index 2 mmio: [0, 0]
[    0.793593] bus: 08 index 3 io port: [0, ffff]
[    0.793595] bus: 08 index 4 mmio: [0, ffffffffffffffff]
[    0.793607] NET: Registered protocol family 2
[    0.832106] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.832760] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.833838] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.834413] TCP: Hash tables configured (established 131072 bind 65536)
[    0.834417] TCP reno registered
[    0.844142] NET: Registered protocol family 1
[    0.844290] checking if image is initramfs... it is
[    1.879113] Freeing initrd memory: 8464k freed
[    1.884057] Simple Boot Flag at 0x36 set to 0x1
[    1.885286] audit: initializing netlink socket (disabled)
[    1.885311] type=2000 audit(1229299446.884:1): initialized
[    1.893168] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.896220] VFS: Disk quotas dquot_6.5.1
[    1.896326] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.896447] msgmni has been set to 1982
[    1.896604] io scheduler noop registered
[    1.896607] io scheduler anticipatory registered
[    1.896609] io scheduler deadline registered
[    1.896753] io scheduler cfq registered (default)
[    1.896768] pci 0000:00:02.0: Boot video device
[    1.897079] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.897135] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.897193] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.897248] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.897296] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.897425] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.897480] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.897534] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.897586] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.897634] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.897765] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.897820] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.897873] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.897921] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.897974] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.898101] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.898155] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.898209] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.898261] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.898309] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.937694] hpet_resources: 0xfed00000 is busy
[    1.937770] Linux agpgart interface v0.103
[    1.937775] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.940459] brd: module loaded
[    1.940549] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.940690] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.941076] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.941163] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.941169] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.941172] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.941175] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.941178] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.961239] mice: PS/2 mouse device common for all mice
[    1.961392] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.961428] rtc0: alarms up to one month, y3k, hpet irqs
[    1.961469] cpuidle: using governor ladder
[    1.961472] cpuidle: using governor menu
[    1.961954] TCP cubic registered
[    1.962193] registered taskstats version 1
[    1.962381]   Magic number: 4:672:51
[    1.962550] rtc_cmos 00:09: setting system clock to 2008-12-15 00:04:08 UTC (1229299448)
[    1.962554] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.962556] EDD information not available.
[    1.962616] Freeing unused kernel memory: 536k freed
[    1.962876] Write protecting the kernel read-only data: 4348k
[    1.964664] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.133174] fuse init (API version 7.9)
[    2.177701] ACPI: SSDT 3F6D0BD1, 01B4 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[    2.178238] ACPI: SSDT 3F6D0A3D, 010F (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[    2.179247] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.179319] processor ACPI0007:00: registered as cooling_device0
[    2.179808] ACPI: SSDT 3F6D0D85, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20060912)
[    2.180316] ACPI: SSDT 3F6D0B4C, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20060912)
[    2.181394] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.181454] processor ACPI0007:01: registered as cooling_device1
[    2.183931] Marking TSC unstable due to TSC halts in idle
[    2.193545] thermal LNXTHERM:01: registered as thermal_zone0
[    2.201447] ACPI: Thermal Zone [TZS0] (26 C)
[    2.206332] thermal LNXTHERM:02: registered as thermal_zone1
[    2.208604] ACPI: Thermal Zone [TZS1] (29 C)
[    2.686771] usbcore: registered new interface driver usbfs
[    2.686800] usbcore: registered new interface driver hub
[    2.686872] usbcore: registered new device driver usb
[    2.689834] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.689852] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.689856] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.689919] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.693836] ehci_hcd 0000:00:1a.7: debug port 1
[    2.693844] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.693863] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4705c00
[    2.697983] USB Universal Host Controller Interface driver v3.0
[    2.709034] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.709202] usb usb1: configuration #1 chosen from 1 choice
[    2.709241] hub 1-0:1.0: USB hub found
[    2.709251] hub 1-0:1.0: 4 ports detected
[    2.759916] No dock devices found.
[    2.783989] SCSI subsystem initialized
[    2.810687] libata version 3.00 loaded.
[    2.813676] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.813689] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.813694] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.813725] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    2.813770] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001840
[    2.813885] usb usb2: configuration #1 chosen from 1 choice
[    2.813917] hub 2-0:1.0: USB hub found
[    2.813926] hub 2-0:1.0: 2 ports detected
[    2.917333] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.917346] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.917351] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.917382] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    2.917428] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001860
[    2.917541] usb usb3: configuration #1 chosen from 1 choice
[    2.917573] hub 3-0:1.0: USB hub found
[    2.917581] hub 3-0:1.0: 2 ports detected
[    3.021514] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.021538] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.021543] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.021575] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.025496] ehci_hcd 0000:00:1d.7: debug port 1
[    3.025504] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.025523] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4706000
[    3.041029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.041200] usb usb4: configuration #1 chosen from 1 choice
[    3.041235] hub 4-0:1.0: USB hub found
[    3.041244] hub 4-0:1.0: 6 ports detected
[    3.249461] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.249474] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.249478] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.249510] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.249544] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    3.249660] usb usb5: configuration #1 chosen from 1 choice
[    3.249693] hub 5-0:1.0: USB hub found
[    3.249701] hub 5-0:1.0: 2 ports detected
[    3.353350] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.353363] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.353368] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.353401] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.353448] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    3.353576] usb usb6: configuration #1 chosen from 1 choice
[    3.353608] hub 6-0:1.0: USB hub found
[    3.353618] hub 6-0:1.0: 2 ports detected
[    3.360050] usb 4-5: new high speed USB device using ehci_hcd and address 2
[    3.456588] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.456601] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.456605] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.456636] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.456671] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    3.456790] usb usb7: configuration #1 chosen from 1 choice
[    3.456824] hub 7-0:1.0: USB hub found
[    3.456832] hub 7-0:1.0: 2 ports detected
[    3.505257] usb 4-5: configuration #1 chosen from 1 choice
[    3.665288] sky2 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.665303] sky2 0000:05:00.0: setting latency timer to 64
[    3.665332] sky2 0000:05:00.0: v1.22 addr 0xf4200000 irq 17 Yukon-2 FE rev 3
[    3.665547] ata_piix 0000:00:1f.1: version 2.12
[    3.665555] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.665600] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.665941] sky2 eth0: addr 00:16:d3:f3:e1:48
[    3.666039] scsi0 : ata_piix
[    3.666760] scsi1 : ata_piix
[    3.667749] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[    3.667754] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[    3.844674] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632M, 0A17, max MWDMA2
[    3.876614] ata1.00: configured for MWDMA2
[    4.000216] Clocksource tsc unstable (delta = -342141709 ns)
[    4.043629] isa bounce pool size: 16 pages
[    4.056701] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632M 0A17 PQ: 0 ANSI: 5
[    4.058453] ahci 0000:00:1f.2: version 3.0
[    4.058474] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.058589] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    4.058593] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    4.058600] ahci 0000:00:1f.2: setting latency timer to 64
[    4.058867] scsi2 : ahci
[    4.058970] scsi3 : ahci
[    4.059058] scsi4 : ahci
[    4.059195] ata3: SATA max UDMA/133 abar m2048@0xf4705000 port 0xf4705100 irq 2298
[    4.059199] ata4: SATA max UDMA/133 abar m2048@0xf4705000 port 0xf4705180 irq 2298
[    4.059203] ata5: SATA max UDMA/133 abar m2048@0xf4705000 port 0xf4705200 irq 2298
[    4.380249] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.381467] ata3.00: _GTF unexpected object type 0x1
[    4.381473] ata3.00: ATA-7: ST9160821AS, 3.BHE, max UDMA/100
[    4.381476] ata3.00: 312581808 sectors, multi 16: LBA48 
[    4.382816] ata3.00: _GTF unexpected object type 0x1
[    4.382826] ata3.00: configured for UDMA/100
[    4.716248] ata4: SATA link down (SStatus 0 SControl 300)
[    5.052249] ata5: SATA link down (SStatus 0 SControl 300)
[    5.068390] scsi 2:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[    5.068596] ohci1394 0000:08:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.121334] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4400000-f44007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.137445] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    5.137493] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.156858] Driver 'sr' needs updating - please use bus_type methods
[    5.166147] Driver 'sd' needs updating - please use bus_type methods
[    5.228588] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.228596] Uniform CD-ROM driver Revision: 3.20
[    5.228774] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.228932] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.228963] sd 2:0:0:0: [sda] Write Protect is off
[    5.228966] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.229013] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.229120] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.229148] sd 2:0:0:0: [sda] Write Protect is off
[    5.229151] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.229203] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.229208]  sda: sda1 sda2 < sda5 >
[    5.270218] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.551456] PM: Starting manual resume from disk
[    5.551460] PM: Resume from partition 8:5
[    5.551462] PM: Checking hibernation image.
[    5.551632] PM: Resume from disk failed.
[    5.612802] kjournald starting.  Commit interval 5 seconds
[    5.612827] EXT3-fs: mounted filesystem with ordered data mode.
[    6.396465] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a00d29d5038]
[   12.949375] udevd version 124 started
[   13.509249] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   13.509889] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   13.535185] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   13.581716] ACPI: WMI: Mapper loaded
[   13.671739] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.708421] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.724572] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.744032] ACPI: Power Button (FF) [PWRF]
[   13.744148] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   13.744988] ACPI: Lid Switch [LID0]
[   13.745079] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.760038] ACPI: Sleep Button (CM) [SLPB]
[   13.799025] acpi device:05: registered as cooling_device2
[   13.799331] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[   13.824052] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.831262] acpi device:0b: registered as cooling_device3
[   13.831771] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input6
[   13.861031] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.079030] ACPI: AC Adapter [ADP1] (off-line)
[   14.191819] ACPI: Battery Slot [BAT0] (battery present)
[   14.825491] ricoh-mmc: Ricoh MMC Controller disabling driver
[   14.825495] ricoh-mmc: Copyright(c) Philip Langdale
[   14.825553] ricoh-mmc: Ricoh MMC controller found at 0000:08:09.2 [1180:0843] (rev 12)
[   14.825579] ricoh-mmc: Controller is now disabled.
[   14.871080] Linux video capture interface: v2.00
[   14.892804] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.892809] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.893091] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.893107] iwl3945 0000:07:00.0: setting latency timer to 64
[   14.893132] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.967800] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.968355] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.985532] iTCO_vendor_support: vendor-support=0
[   15.024809] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   15.117725] sdhci: Secure Digital Host Controller Interface driver
[   15.117729] sdhci: Copyright(c) Pierre Ossman
[   15.139643] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
[   15.179293] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.179333] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.181725] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   15.210976] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   15.211232] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   15.211343] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.242002] iwl3945 0000:07:00.0: PCI INT A disabled
[   15.242821] sdhci-pci 0000:08:09.1: SDHCI controller found [1180:0822] (rev 22)
[   15.242839] sdhci-pci 0000:08:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.245906] mmc0: SDHCI controller on PCI [0000:08:09.1] using PIO
[   15.276222] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b016)
[   15.290551] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb4/4-5/4-5:1.0/input/input10
[   15.572233] usbcore: registered new interface driver uvcvideo
[   15.572238] USB Video Class driver (v0.1.0)
[   16.974775] lp: driver loaded but no devices found
[   17.227268] Adding 2971984k swap on /dev/sda5.  Priority:-1 extents:1 across:2971984k
[   17.257199] EXT3 FS on sda1, internal journal
[   17.843513] type=1505 audit(1229299464.121:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4209
[   18.039328] type=1505 audit(1229299464.317:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4214
[   18.039552] type=1505 audit(1229299464.317:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4214
[   18.205077] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.173781] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.433745] ppdev: user-space parallel port driver
[   23.175865] Bluetooth: Core ver 2.13
[   23.177478] NET: Registered protocol family 31
[   23.177487] Bluetooth: HCI device and connection manager initialized
[   23.177492] Bluetooth: HCI socket layer initialized
[   23.229353] Bluetooth: L2CAP ver 2.11
[   23.229362] Bluetooth: L2CAP socket layer initialized
[   23.242538] Bluetooth: SCO (Voice Link) ver 0.6
[   23.242549] Bluetooth: SCO socket layer initialized
[   23.255428] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.255439] Bluetooth: BNEP filters: protocol multicast
[   23.302202] Bridge firewalling registered
[   23.303971] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   23.398293] Bluetooth: RFCOMM socket layer initialized
[   23.398573] Bluetooth: RFCOMM TTY layer initialized
[   23.398582] Bluetooth: RFCOMM ver 1.10
[   27.533550] sky2 eth0: enabling interface
[   27.563630] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   27.563799] iwl3945 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.564108] firmware: requesting iwlwifi-3945-1.ucode
[   27.720550] Registered led device: iwl-phy0:radio
[   27.720626] Registered led device: iwl-phy0:assoc
[   27.720648] Registered led device: iwl-phy0:RX
[   27.720668] Registered led device: iwl-phy0:TX
[   27.815513] NET: Registered protocol family 17
[   27.863082] [drm] Initialized drm 1.1.0 20060810
[   27.880630] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.880649] pci 0000:00:02.0: setting latency timer to 64
[   27.881931] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.584283] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[   30.586604] wlan0: authenticated
[   30.586615] wlan0: associate with AP 00:13:46:f5:cc:b2
[   30.589723] wlan0: RX AssocResp from 00:13:46:f5:cc:b2 (capab=0x421 status=0 aid=2)
[   30.589732] wlan0: associated
[   30.597316] wlan0: disassociating by local choice (reason=3)
[   52.655619] wlan0: deauthenticated
[   52.656350] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[   52.658587] wlan0: authenticated
[   52.658596] wlan0: associate with AP 00:13:46:f5:cc:b2
[   52.661410] wlan0: RX ReassocResp from 00:13:46:f5:cc:b2 (capab=0x421 status=0 aid=2)
[   52.661419] wlan0: associated
[   52.661949] wlan0: disassociating by local choice (reason=3)
[   85.508065] ACPI: EC: missing confirmations, switch off interrupt mode.
[   86.008154] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[   86.008182] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.TZS1._TMP] (Node ffff88003f1b6580), AE_TIME
[   88.685152] CE: hpet increasing min_delta_ns to 15000 nsec
[   97.511034] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[   97.512874] wlan0: authenticated
[   97.512888] wlan0: associate with AP 00:13:46:f5:cc:b2
[   97.517458] wlan0: RX ReassocResp from 00:13:46:f5:cc:b2 (capab=0x421 status=0 aid=2)
[   97.517472] wlan0: associated
[   97.945209] CPU0 attaching NULL sched-domain.
[   97.945228] CPU1 attaching NULL sched-domain.
[   97.960209] CPU0 attaching sched-domain:
[   97.960220]  domain 0: span 0-1 level MC
[   97.960225]   groups: 0 1
[   97.960233]   domain 1: span 0-1 level CPU
[   97.960236]    groups: 0-1
[   97.960242]    domain 2: span 0-1 level NODE
[   97.960246]     groups: 0-1
[   97.960253] CPU1 attaching sched-domain:
[   97.960257]  domain 0: span 0-1 level MC
[   97.960260]   groups: 1 0
[   97.960266]   domain 1: span 0-1 level CPU
[   97.960270]    groups: 0-1
[   97.960275]    domain 2: span 0-1 level NODE
[   97.960278]     groups: 0-1
[  484.292379] NET: Registered protocol family 10
[  484.294561] lo: Disabled Privacy Extensions
[  484.296548] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  494.841166] wlan0: no IPv6 routers present
[  532.832163] wlan0: No ProbeResp from current AP 00:13:46:f5:cc:b2 - assume out of range
[  533.741155] CE: hpet increasing min_delta_ns to 22500 nsec
[  548.063282] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  548.260253] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  548.460305] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  548.660195] wlan0: authentication with AP 00:13:46:f5:cc:b2 timed out
[  573.095648] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  573.292098] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  573.492043] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  573.692034] wlan0: authentication with AP 00:13:46:f5:cc:b2 timed out
[  581.667811] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  581.864064] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  582.064043] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  582.264152] wlan0: authentication with AP 00:13:46:f5:cc:b2 timed out
[  610.681040] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  610.884075] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  611.080159] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  611.280076] wlan0: authentication with AP 00:13:46:f5:cc:b2 timed out
[  643.204866] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  643.400833] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  643.600122] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[  643.802717] wlan0: authentication with AP 00:13:46:f5:cc:b2 timed out
[  823.141154] CE: hpet increasing min_delta_ns to 33750 nsec
[ 1543.965195] wlan0: authenticate with AP 00:13:46:f5:cc:b2
[ 1543.967027] wlan0: authenticated
[ 1543.967040] wlan0: associate with AP 00:13:46:f5:cc:b2
[ 1543.969876] wlan0: RX AssocResp from 00:13:46:f5:cc:b2 (capab=0x421 status=0 aid=2)
[ 1543.969887] wlan0: associated
[ 1598.599585] end_request: I/O error, dev sr0, sector 1195160
[ 1598.599602] Buffer I/O error on device sr0, logical block 149395
[ 1600.324120] end_request: I/O error, dev sr0, sector 1195160
[ 1600.324136] Buffer I/O error on device sr0, logical block 149395
[ 1600.466224] end_request: I/O error, dev sr0, sector 0
[ 1600.466240] Buffer I/O error on device sr0, logical block 0
[ 1600.466251] Buffer I/O error on device sr0, logical block 1
[ 1600.466256] Buffer I/O error on device sr0, logical block 2
[ 1600.466260] Buffer I/O error on device sr0, logical block 3
[ 1600.467501] end_request: I/O error, dev sr0, sector 0
[ 1600.467506] Buffer I/O error on device sr0, logical block 0
[ 1603.042445] UDF-fs: No VRS found
[ 1603.313599] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1603.314941] ISOFS: changing to secondary root

```

---

### Post by grimey44 on 2008-12-14
then when its frozen i tried the ctrl+alt+bckspc command and it went back to the login. i enterd info then it goes to my desktop but doesnt load any thing else except the desktop image and the cursor. then i have to hold down the power to get it to shut it off.

---

### Post by lordbux on 2008-12-15
mmmmmmmmmmmmmmmmmmmmmmmmmmm

i think its with the drive.... 
feels as if its not responding to the kernel rhythm

[b]BUT SEE THIS FIRST

have you updated  your system ..... else run a fill update

did you drag and drop to coppy files ===> this can put the buffer system under preasure try manual coppying using right click or  using terminal.

actually desktop items not loading means that the support tools failed to load...this is often due to flaw in the graphical tool..
how ever using the terminal to copy file will solve it if that is the problem.

use the *cp* command to copy [/b]


hoping for good new
long live opensource

---

### Post by lordbux on 2008-12-15
actually the command is not lapci

its ```
lspci
```

really sorry for the  ...

would you mind running it

---

### Post by gjoellee on 2008-12-15
tried right clicking on the CD icon that appears on your desktop and click on "Eject Volume"?

---

### Post by 3rdalbum on 2008-12-15
"Buffer I/O error" means that the disc is unreadable, or the drive is faulty.

---

### Post by grimey44 on 2008-12-15
here is the output for the command "lspci"

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

i dont think its the drive being faulty cause it worked fine in windows.
and the disks ive tried were Just burned.

also, i normally dont drag and drop, i use the right click copy/paste.
but im not sure how to copy using terminal.

I went to update manager and it says my system is up to date. is there another way to update things? because i have a number of problems with ubuntu. my sony mp3 player wont work, nor will my sony memorystick duo.

thanx for all your help

---

### Post by grimey44 on 2008-12-16
anybody have any ideas??

---

### Post by lordbux on 2008-12-17
[B]sony's Walkman mp3 players are built for windows they wont work
no surprise . make sure that you have swiched of the memmory stick's security tool before you plug it in.

mmmm it seems your entire system is in tough situation 
.some thing is corrupt .....let me try to figure out
k ..... 

which is ur ubuntu version 

did you try to upgrade from an older version to new 
eg: from ubuntu 7 to 8
(dont do it always look for fresh install)
[/B]

---

### Post by grimey44 on 2008-12-17
i dont think my memory card has a security switch.


so ive got  version 8.10
i didnt upgrade, i had vista befor and got my current version. Ialso dont have a partition. just ubuntu now.
the install seemed to work fine. theres just some things that seem like they need fixing. and i appreciate your help

---

### Post by grimey44 on 2008-12-18
any ideas??

---

### Post by editrix on 2008-12-19
Well, these are just ideas.

I know there have been huge CD burning/ejecting problems in Ubuntu for some time. I've been wondering if they've been fixed for Intrepid--which I don't use. I posted some info on the issue here: [http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)

Regarding just ejecting the CD, you could try:

```
$ sudo fuser -k /media/cdrom0 
```

then

```
$ eject
```

This works for me maybe 50% of the time.

---

