---
title: "Mounting ZIP Drive"
date: 2006-07-09
forum: Desktop Environments
---

### Post by ssmithy on 2006-07-09
I'm trying very hard to get an Iomega 100 MB ZIP drive using a paralell port to mount in Dapper.  I went through several howtos in these forumns and in other places and got so-so results. Here's what I did.  I'm hoping someone can see an error in my ways and give me a push in the right direction. :)

First I added the line "ppa" to the /etc/modules, as was discussed in several places that this module needs to be loaded.

Then a created a directory for the device: /mnt/zip100.0

After that I added the following line to my /etc/fstab:

/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0

Rebooted.  The device shows up alongside my floppy and cdrom but gives me an error message when I try to mount:

mount: special device /dev/sda4 does not exist

I ran dmesg but it doesn't list anything related the ZIP drive.  If anyone has any input it would be greatly appreciated.  This is for my father's computer and I've been slowly weening him away from windows.  If I could get this up and running (he loves his Zip disks) I might be able to switch him over entirely.

Thanks!

---

### Post by taurus on 2006-07-09
Look in /var/log/messages to see if your kernel sees it and what device it is...  It may not be /dev/sda4!!!
```

sudo more /var/log/messages

```

---

### Post by ssmithy on 2006-07-09
I doesn't list the device.  The only thing I could find in the log posibbly related to this is:


Jul  9 16:43:50 localhost kernel: [17179595.244000] lp0: using parport0 (interrupt-driven)

and

Jul  9 16:43:50 localhost kernel: [17179595.332000] ppa: Version 2.07 (for Linux 2.4.x)

I chose /dev/sda4 because aparently thats how Iomega names it's devices:

First Iomega Drive to Initialize  	/dev/sda4
Second Iomega Drive to Initialize 	/dev/sdb4
Third Iomega Drive to Initialize 	/dev/sdc4
Fourth Iomega Drive to Initialize 	/dev/sdd4

source: [http://www.iomega.com/support/manuals/linux_cli/cli.html](http://www.iomega.com/support/manuals/linux_cli/cli.html)

---

### Post by taurus on 2006-07-09
If you connect it to a parallel port, turn it on, and boot Dapper, the kernel will try to assign a device name to it!  It could use a difference name than Iomega so that's why you need to look in /var/log/messages or dmesg...  Try to clear /var/log/messages first with
```

sudo cat /dev/null > /var/log/messages

```
Now, reboot and then paste the latest output of /var/log/messages here...
```

sudo more /var/log/messages

```

---

### Post by ssmithy on 2006-07-09
```
Jul  9 17:35:36 localhost exiting on signal 15
Jul  9 17:36:30 localhost syslogd 1.4.1#17ubuntu7: restart.
Jul  9 17:36:31 localhost kernel: Inspecting /boot/System.map-2.6.15-25-386
Jul  9 17:36:31 localhost kernel: Loaded 23020 symbols from /boot/System.map-2.6
.15-25-386.
Jul  9 17:36:31 localhost kernel: Symbols match kernel version 2.6.15.
Jul  9 17:36:31 localhost kernel: No module symbols loaded - kernel modules not
enabled.
Jul  9 17:36:31 localhost kernel: [17179569.184000] Linux version 2.6.15-25-386
(buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Ju
n 14 11:25:49 UTC 2006
Jul  9 17:36:31 localhost kernel: [17179569.184000] BIOS-provided physical RAM m
ap:
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000
 - 00000000000a0000 (usable)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000f0000
 - 0000000000100000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000
 - 000000001fe70000 (usable)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 000000001fe70000
 - 000000001fe72000 (ACPI NVS)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 000000001fe72000
 - 000000001fe93000 (ACPI data)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 000000001fe93000
 - 000000001ff00000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000
 - 00000000fec10000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fecf0000
 - 00000000fecf1000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fed20000
 - 00000000fed90000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000
 - 00000000fee10000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ffb00000
 - 0000000100000000 (reserved)
Jul  9 17:36:31 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Jul  9 17:36:31 localhost kernel: [17179569.184000] 510MB LOWMEM available.
Jul  9 17:36:31 localhost kernel: [17179569.184000] found SMP MP-table at 000fe7
10
Jul  9 17:36:31 localhost kernel: [17179569.184000] DMI 2.3 present.
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x80
8
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] l
apic_id[0x00] enabled)
Jul  9 17:36:31 localhost kernel: [17179569.184000] Processor #0 15:4 APIC versi
on 20
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x02] l
apic_id[0x01] disabled)
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x03] l
apic_id[0x01] disabled)
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x04] l
apic_id[0x03] disabled)
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] addre
ss[0xfec00000] gsi_base[0])
Jul  9 17:36:31 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 1, versio
n 32, address 0xfec00000, GSI 0-23
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus
_irq 0 global_irq 2 dfl dfl)
Jul  9 17:36:31 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus
_irq 9 global_irq 9 high level)
Jul  9 17:36:31 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.
Using 1 I/O APICs
Jul  9 17:36:31 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP co
nfiguration information
Jul  9 17:36:31 localhost kernel: [17179569.184000] Allocating PCI resources sta
rting at 20000000 (gap: 1ff00000:ded00000)
Jul  9 17:36:31 localhost kernel: [17179569.184000] Built 1 zonelists
Jul  9 17:36:31 localhost kernel: [17179569.184000] Kernel command line: root=/d
ev/hda1 ro quiet splash
Jul  9 17:36:31 localhost kernel: [17179569.184000] Initializing CPU#0
Jul  9 17:36:31 localhost kernel: [17179569.184000] PID hash table entries: 2048
 (order: 11, 32768 bytes)
Jul  9 17:36:31 localhost kernel: [17179569.184000] Detected 2394.617 MHz proces
sor.
Jul  9 17:36:31 localhost kernel: [17179569.184000] Using pmtmr for high-res tim
esource
Jul  9 17:36:31 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Jul  9 17:36:31 localhost kernel: [17179573.168000] Dentry cache hash table entr
ies: 65536 (order: 6, 262144 bytes)
Jul  9 17:36:31 localhost kernel: [17179573.172000] Inode-cache hash table entri
es: 32768 (order: 5, 131072 bytes)
Jul  9 17:36:31 localhost kernel: [17179573.180000] Memory: 507700k/522688k avai
lable (1976k kernel code, 14408k reserved, 606k data, 288k init, 0k highmem)
Jul  9 17:36:31 localhost kernel: [17179573.180000] Checking if this processor h
onours the WP bit even in supervisor mode... Ok.
Jul  9 17:36:31 localhost kernel: [17179573.260000] Calibrating delay using time
r specific routine.. 4793.23 BogoMIPS (lpj=9586468)
Jul  9 17:36:31 localhost kernel: [17179573.260000] Security Framework v1.0.0 in
itialized
Jul  9 17:36:31 localhost kernel: [17179573.260000] SELinux:  Disabled at boot.
Jul  9 17:36:31 localhost kernel: [17179573.260000] Mount-cache hash table entri
es: 512
Jul  9 17:36:31 localhost kernel: [17179573.260000] monitor/mwait feature presen
t.
Jul  9 17:36:31 localhost kernel: [17179573.260000] using mwait in idle threads.
Jul  9 17:36:31 localhost kernel: [17179573.260000] CPU: Trace cache: 12K uops,
L1 D cache: 16K
Jul  9 17:36:31 localhost kernel: [17179573.260000] CPU: L2 cache: 256K
Jul  9 17:36:31 localhost kernel: [17179573.260000] mtrr: v2.0 (20020519)
Jul  9 17:36:31 localhost kernel: [17179573.260000] CPU: Intel(R) Celeron(R) CPU
 2.40GHz stepping 01
Jul  9 17:36:31 localhost kernel: [17179573.260000] Enabling fast FPU save and r
estore... done.
Jul  9 17:36:31 localhost kernel: [17179573.260000] Enabling unmasked SIMD FPU e
xception support... done.
Jul  9 17:36:31 localhost kernel: [17179573.260000] Checking 'hlt' instruction..
. OK.
Jul  9 17:36:31 localhost kernel: [17179573.276000] checking if image is initram
fs... it is
Jul  9 17:36:31 localhost kernel: [17179573.908000] Freeing initrd memory: 6613k
 freed
Jul  9 17:36:31 localhost kernel: [17179573.920000] ACPI: Looking for DSDT ... n
ot found!
Jul  9 17:36:31 localhost kernel: [17179573.948000] ENABLING IO-APIC IRQs
Jul  9 17:36:31 localhost kernel: [17179573.948000] ..TIMER: vector=0x31 apic1=0
 pin1=2 apic2=-1 pin2=-1
Jul  9 17:36:31 localhost kernel: [17179574.092000] NET: Registered protocol fam
ily 16
Jul  9 17:36:31 localhost kernel: [17179574.092000] EISA bus registered
Jul  9 17:36:31 localhost kernel: [17179574.092000] ACPI: bus type pci registere
d
Jul  9 17:36:31 localhost kernel: [17179574.104000] PCI: PCI BIOS revision 2.10
entry at 0xfbbf8, last bus=1
Jul  9 17:36:31 localhost kernel: [17179574.104000] PCI: Using configuration typ
e 1
Jul  9 17:36:31 localhost kernel: [17179574.104000] ACPI: Subsystem revision 200
51216
Jul  9 17:36:31 localhost kernel: [17179574.140000] ACPI: Interpreter enabled
Jul  9 17:36:31 localhost kernel: [17179574.140000] ACPI: Using IOAPIC for inter
rupt routing
Jul  9 17:36:31 localhost kernel: [17179574.144000] ACPI: PCI Root Bridge [PCI0]
 (0000:00)
Jul  9 17:36:31 localhost kernel: [17179574.148000] ACPI: Assume root bridge [\_
SB_.PCI0] bus is 0
Jul  9 17:36:31 localhost kernel: [17179574.164000] PCI quirk: region 0800-087f
claimed by ICH4 ACPI/GPIO/TCO
Jul  9 17:36:31 localhost kernel: [17179574.164000] PCI quirk: region 0880-08bf
claimed by ICH4 GPIO
Jul  9 17:36:31 localhost kernel: [17179574.164000] PCI: Ignoring BAR0-3 of IDE
controller 0000:00:1f.1
Jul  9 17:36:31 localhost kernel: [17179574.164000] PCI: Transparent bridge - 00
00:00:1e.0
Jul  9 17:36:31 localhost kernel: [17179574.344000] ACPI: PCI Interrupt Link [LN
KA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.344000] ACPI: PCI Interrupt Link [LN
KB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.344000] ACPI: PCI Interrupt Link [LN
KC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.348000] ACPI: PCI Interrupt Link [LN
KD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.348000] ACPI: PCI Interrupt Link [LN
KE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.348000] ACPI: PCI Interrupt Link [LN
KF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul  9 17:36:31 localhost kernel: [17179574.348000] ACPI: PCI Interrupt Link [LN
KG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.352000] ACPI: PCI Interrupt Link [LN
KH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Jul  9 17:36:31 localhost kernel: [17179574.352000] Linux Plug and Play Support
v0.97 (c) Adam Belay
Jul  9 17:36:31 localhost kernel: [17179574.352000] pnp: PnP ACPI init
Jul  9 17:36:31 localhost kernel: [17179574.384000] pnp: PnP ACPI: found 11 devi
ces
Jul  9 17:36:31 localhost kernel: [17179574.384000] PnPBIOS: Disabled by ACPI PN
P
Jul  9 17:36:31 localhost kernel: [17179574.384000] PCI: Using ACPI for IRQ rout
ing
Jul  9 17:36:31 localhost kernel: [17179574.384000] PCI: If a device doesn't wor
k, try "pci=routeirq".  If it helps, post a report
Jul  9 17:36:31 localhost kernel: [17179574.396000] pnp: 00:0a: ioport range 0x8
00-0x85f could not be reserved
Jul  9 17:36:31 localhost kernel: [17179574.396000] pnp: 00:0a: ioport range 0xc
00-0xc7f has been reserved
Jul  9 17:36:31 localhost kernel: [17179574.396000] pnp: 00:0a: ioport range 0x8
60-0x8ff could not be reserved
Jul  9 17:36:31 localhost kernel: [17179574.396000] PCI: Ignore bogus resource 6
 [0:0] of 0000:00:02.0
Jul  9 17:36:31 localhost kernel: [17179574.396000] PCI: Bridge: 0000:00:1e.0
Jul  9 17:36:31 localhost kernel: [17179574.396000]   IO window: d000-dfff
Jul  9 17:36:31 localhost kernel: [17179574.396000]   MEM window: fea00000-feaff
fff
Jul  9 17:36:31 localhost kernel: [17179574.396000]   PREFETCH window: disabled.
Jul  9 17:36:31 localhost kernel: [17179574.396000] Simple Boot Flag value 0x87
read from CMOS RAM was invalid
Jul  9 17:36:31 localhost kernel: [17179574.396000] Simple Boot Flag at 0x7a set
 to 0x1
Jul  9 17:36:31 localhost kernel: [17179574.396000] audit: initializing netlink
socket (disabled)
Jul  9 17:36:31 localhost kernel: [17179574.396000] audit(1152484566.396:1): ini
tialized
Jul  9 17:36:31 localhost kernel: [17179574.396000] VFS: Disk quotas dquot_6.5.1
Jul  9 17:36:31 localhost kernel: [17179574.396000] Dquot-cache hash table entri
es: 1024 (order 0, 4096 bytes)
Jul  9 17:36:31 localhost kernel: [17179574.396000] Initializing Cryptographic A
PI
Jul  9 17:36:31 localhost kernel: [17179574.396000] io scheduler noop registered
Jul  9 17:36:31 localhost kernel: [17179574.396000] io scheduler anticipatory re
gistered
Jul  9 17:36:31 localhost kernel: [17179574.396000] io scheduler deadline regist
ered
Jul  9 17:36:31 localhost kernel: [17179574.396000] io scheduler cfq registered
Jul  9 17:36:31 localhost kernel: [17179574.396000] isapnp: Scanning for PnP car
ds...
Jul  9 17:36:31 localhost kernel: [17179574.748000] isapnp: No Plug & Play devic
e found
Jul  9 17:36:31 localhost kernel: [17179574.772000] PNP: PS/2 Controller [PNP030
3:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul  9 17:36:31 localhost kernel: [17179574.776000] serio: i8042 AUX port at 0x6
0,0x64 irq 12
Jul  9 17:36:31 localhost kernel: [17179574.776000] serio: i8042 KBD port at 0x6
0,0x64 irq 1
Jul  9 17:36:31 localhost kernel: [17179574.776000] Serial: 8250/16550 driver $R
evision: 1.90 $ 48 ports, IRQ sharing enabled
Jul  9 17:36:31 localhost kernel: [17179574.776000] serial8250: ttyS0 at I/O 0x3
f8 (irq = 4) is a 16550A
Jul  9 17:36:31 localhost kernel: [17179574.780000] 00:08: ttyS0 at I/O 0x3f8 (i
rq = 4) is a 16550A
Jul  9 17:36:31 localhost kernel: [17179574.780000] RAMDISK driver initialized:
16 RAM disks of 65536K size 1024 blocksize
Jul  9 17:36:31 localhost kernel: [17179574.780000] Uniform Multi-Platform E-IDE
 driver Revision: 7.00alpha2
Jul  9 17:36:31 localhost kernel: [17179574.780000] ide: Assuming 33MHz system b
us speed for PIO modes; override with idebus=xx
Jul  9 17:36:31 localhost kernel: [17179574.780000] mice: PS/2 mouse device comm
on for all mice
Jul  9 17:36:31 localhost kernel: [17179574.784000] EISA: Probing bus 0 at eisa.
0
Jul  9 17:36:31 localhost kernel: [17179574.784000] EISA: Detected 0 cards.
Jul  9 17:36:31 localhost kernel: [17179574.784000] NET: Registered protocol fam
ily 2
Jul  9 17:36:31 localhost kernel: [17179574.812000] input: AT Translated Set 2 k
eyboard as /class/input/input0
Jul  9 17:36:31 localhost kernel: [17179574.824000] IP route cache hash table en
tries: 4096 (order: 2, 16384 bytes)
Jul  9 17:36:31 localhost kernel: [17179574.824000] TCP established hash table e
ntries: 16384 (order: 4, 65536 bytes)
Jul  9 17:36:31 localhost kernel: [17179574.824000] TCP bind hash table entries:
 16384 (order: 4, 65536 bytes)
Jul  9 17:36:31 localhost kernel: [17179574.824000] TCP: Hash tables configured
(established 16384 bind 16384)
Jul  9 17:36:31 localhost kernel: [17179574.824000] TCP reno registered
Jul  9 17:36:31 localhost kernel: [17179574.824000] TCP bic registered
Jul  9 17:36:31 localhost kernel: [17179574.824000] NET: Registered protocol fam
ily 1
Jul  9 17:36:31 localhost kernel: [17179574.824000] NET: Registered protocol fam
ily 8
Jul  9 17:36:31 localhost kernel: [17179574.824000] NET: Registered protocol fam
ily 20
Jul  9 17:36:31 localhost kernel: [17179574.824000] Using IPI Shortcut mode
Jul  9 17:36:31 localhost kernel: [17179574.824000] ACPI wakeup devices:
Jul  9 17:36:31 localhost kernel: [17179574.824000] VBTN PCI0 USB0 USB1 USB2 USB
3 PCI1  KBD
Jul  9 17:36:31 localhost kernel: [17179574.824000] ACPI: (supports S0 S1 S3 S4
S5)
Jul  9 17:36:31 localhost kernel: [17179574.824000] Freeing unused kernel memory
: 288k freed
Jul  9 17:36:31 localhost kernel: [17179574.876000] vga16fb: mapped to 0xc00a000
0
Jul  9 17:36:31 localhost kernel: [17179574.996000] Console: switching to colour
 frame buffer device 80x25
Jul  9 17:36:31 localhost kernel: [17179574.996000] fb0: VGA16 VGA frame buffer
device
Jul  9 17:36:31 localhost kernel: [17179576.092000] Capability LSM initialized
Jul  9 17:36:31 localhost kernel: [17179576.808000] ICH5: IDE controller at PCI
slot 0000:00:1f.1
Jul  9 17:36:31 localhost kernel: [17179576.808000] ACPI: PCI Interrupt 0000:00:
1f.1[A] -> GSI 18 (level, low) -> IRQ 169
Jul  9 17:36:31 localhost kernel: [17179576.808000] ICH5: chipset revision 2
Jul  9 17:36:31 localhost kernel: [17179576.808000] ICH5: not 100%% native mode:
 will probe irqs later
Jul  9 17:36:31 localhost kernel: [17179576.808000]     ide0: BM-DMA at 0xffa0-0
xffa7, BIOS settings: hda:DMA, hdb:pio
Jul  9 17:36:31 localhost kernel: [17179576.808000]     ide1: BM-DMA at 0xffa8-0
xffaf, BIOS settings: hdc:DMA, hdd:DMA
Jul  9 17:36:31 localhost kernel: [17179577.096000] hda: SAMSUNG SP0802N, ATA DI
SK drive
Jul  9 17:36:31 localhost kernel: [17179577.768000] ide0 at 0x1f0-0x1f7,0x3f6 on
 irq 14
Jul  9 17:36:31 localhost kernel: [17179578.508000] hdc: SONY DVD-ROM DDU1615, A
TAPI CD/DVD-ROM drive
Jul  9 17:36:31 localhost kernel: [17179578.956000] hdd: SONY CD-RW CRX216E, ATA
PI CD/DVD-ROM drive
Jul  9 17:36:31 localhost kernel: [17179579.012000] ide1 at 0x170-0x177,0x376 on
 irq 15
Jul  9 17:36:31 localhost kernel: [17179579.024000] hda: max request size: 1024K
iB
Jul  9 17:36:31 localhost kernel: [17179579.040000] hda: Host Protected Area det
ected.
Jul  9 17:36:31 localhost kernel: [17179579.040000] ^Icurrent capacity is 156250
000 sectors (80000 MB)
Jul  9 17:36:31 localhost kernel: [17179579.040000] ^Inative  capacity is 156368
016 sectors (80060 MB)
Jul  9 17:36:31 localhost kernel: [17179579.040000] hda: Host Protected Area dis
abled.
Jul  9 17:36:31 localhost kernel: [17179579.040000] hda: 156368016 sectors (8006
0 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
Jul  9 17:36:31 localhost kernel: [17179579.040000] hda: cache flushes supported
Jul  9 17:36:31 localhost kernel: [17179579.040000]  hda: hda1 hda2 < hda5 >
Jul  9 17:36:31 localhost kernel: [17179579.080000] hdc: ATAPI 48X DVD-ROM drive
, 254kB Cache, UDMA(33)
Jul  9 17:36:31 localhost kernel: [17179579.080000] Uniform CD-ROM driver Revisi
on: 3.20
Jul  9 17:36:31 localhost kernel: [17179579.096000] hdd: ATAPI 48X CD-ROM CD-R/R
W drive, 2048kB Cache, UDMA(33)
Jul  9 17:36:31 localhost kernel: [17179579.280000] usbcore: registered new driv
er usbfs
Jul  9 17:36:31 localhost kernel: [17179579.280000] usbcore: registered new driv
er hub
Jul  9 17:36:31 localhost kernel: [17179579.280000] USB Universal Host Controlle
r Interface driver v2.3
Jul  9 17:36:31 localhost kernel: [17179579.280000] ACPI: PCI Interrupt 0000:00:
1d.0[A] -> GSI 16 (level, low) -> IRQ 177
Jul  9 17:36:31 localhost kernel: [17179579.280000] uhci_hcd 0000:00:1d.0: UHCI
Host Controller
Jul  9 17:36:31 localhost kernel: [17179579.280000] uhci_hcd 0000:00:1d.0: new U
SB bus registered, assigned bus number 1
Jul  9 17:36:31 localhost kernel: [17179579.280000] uhci_hcd 0000:00:1d.0: irq 1
77, io base 0x0000ff80
Jul  9 17:36:31 localhost kernel: [17179579.280000] hub 1-0:1.0: USB hub found
Jul  9 17:36:31 localhost kernel: [17179579.280000] hub 1-0:1.0: 2 ports detecte
d
Jul  9 17:36:31 localhost kernel: [17179579.384000] ACPI: PCI Interrupt 0000:00:
1d.1[B] -> GSI 19 (level, low) -> IRQ 185
Jul  9 17:36:31 localhost kernel: [17179579.384000] uhci_hcd 0000:00:1d.1: UHCI
Host Controller
Jul  9 17:36:31 localhost kernel: [17179579.384000] uhci_hcd 0000:00:1d.1: new U
SB bus registered, assigned bus number 2
Jul  9 17:36:31 localhost kernel: [17179579.384000] uhci_hcd 0000:00:1d.1: irq 1
85, io base 0x0000ff60
Jul  9 17:36:31 localhost kernel: [17179579.384000] hub 2-0:1.0: USB hub found
Jul  9 17:36:31 localhost kernel: [17179579.384000] hub 2-0:1.0: 2 ports detecte
d
Jul  9 17:36:31 localhost kernel: [17179579.488000] ACPI: PCI Interrupt 0000:00:
1d.3[A] -> GSI 16 (level, low) -> IRQ 177
Jul  9 17:36:31 localhost kernel: [17179579.488000] uhci_hcd 0000:00:1d.3: UHCI
Host Controller
Jul  9 17:36:31 localhost kernel: [17179579.488000] uhci_hcd 0000:00:1d.3: new U
SB bus registered, assigned bus number 3
Jul  9 17:36:31 localhost kernel: [17179579.488000] uhci_hcd 0000:00:1d.3: irq 1
77, io base 0x0000ff20
Jul  9 17:36:31 localhost kernel: [17179579.488000] hub 3-0:1.0: USB hub found
Jul  9 17:36:31 localhost kernel: [17179579.488000] hub 3-0:1.0: 2 ports detecte
d
Jul  9 17:36:31 localhost kernel: [17179579.592000] ACPI: PCI Interrupt 0000:00:
1d.7[D] -> GSI 23 (level, low) -> IRQ 193
Jul  9 17:36:31 localhost kernel: [17179579.592000] ehci_hcd 0000:00:1d.7: EHCI
Host Controller
Jul  9 17:36:31 localhost kernel: [17179579.592000] ehci_hcd 0000:00:1d.7: debug
 port 1
Jul  9 17:36:31 localhost kernel: [17179579.592000] ehci_hcd 0000:00:1d.7: new U
SB bus registered, assigned bus number 4
Jul  9 17:36:31 localhost kernel: [17179579.592000] ehci_hcd 0000:00:1d.7: irq 1
93, io mem 0xffa80800
Jul  9 17:36:31 localhost kernel: [17179579.596000] ehci_hcd 0000:00:1d.7: USB 2
.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  9 17:36:31 localhost kernel: [17179579.596000] hub 4-0:1.0: USB hub found
Jul  9 17:36:31 localhost kernel: [17179579.596000] hub 4-0:1.0: 8 ports detecte
d
Jul  9 17:36:31 localhost kernel: [17179579.824000] Attempting manual resume
Jul  9 17:36:31 localhost kernel: [17179579.892000] EXT3-fs: mounted filesystem
with ordered data mode.
Jul  9 17:36:31 localhost kernel: [17179579.892000] kjournald starting.  Commit
interval 5 seconds
Jul  9 17:36:31 localhost kernel: [17179591.348000] pci_hotplug: PCI Hot Plug PC
I Core version: 0.5
Jul  9 17:36:31 localhost kernel: [17179591.352000] shpchp: Standard Hot Plug PC
I Controller Driver version: 0.4
Jul  9 17:36:31 localhost kernel: [17179591.380000] hw_random hardware driver 1.
0.0 loaded
Jul  9 17:36:31 localhost kernel: [17179591.452000] Linux agpgart interface v0.1
01 (c) Dave Jones
Jul  9 17:36:31 localhost kernel: [17179591.456000] agpgart: Detected an Intel 8
65 Chipset.
Jul  9 17:36:31 localhost kernel: [17179591.456000] agpgart: Detected 892K stole
n memory.
Jul  9 17:36:31 localhost kernel: [17179591.472000] agpgart: AGP aperture is 128
M @ 0xe8000000
Jul  9 17:36:31 localhost kernel: [17179591.900000] input: PC Speaker as /class/
input/input1
Jul  9 17:36:31 localhost kernel: [17179592.052000] ACPI: PCI Interrupt 0000:00:
1f.5[B] -> GSI 17 (level, low) -> IRQ 201
Jul  9 17:36:31 localhost kernel: [17179592.124000] e100: Intel(R) PRO/100 Netwo
rk Driver, 3.4.14-k4-NAPI
Jul  9 17:36:31 localhost kernel: [17179592.124000] e100: Copyright(c) 1999-2005
 Intel Corporation
Jul  9 17:36:31 localhost kernel: [17179592.280000] Floppy drive(s): fd0 is 1.44
M
Jul  9 17:36:31 localhost kernel: [17179592.296000] FDC 0 is a post-1991 82077
Jul  9 17:36:31 localhost kernel: [17179592.372000] intel8x0_measure_ac97_clock:
 measured 55589 usecs
Jul  9 17:36:31 localhost kernel: [17179592.372000] intel8x0: clocking to 48000
Jul  9 17:36:31 localhost kernel: [17179592.372000] ACPI: PCI Interrupt 0000:01:
08.0[A] -> GSI 20 (level, low) -> IRQ 209
Jul  9 17:36:31 localhost kernel: [17179592.392000] e100: eth0: e100_probe: addr
 0xfeaef000, irq 209, MAC addr 00:13:20:46:D6:40
Jul  9 17:36:31 localhost kernel: [17179592.500000] Real Time Clock Driver v1.12
Jul  9 17:36:31 localhost kernel: [17179592.568000] parport: PnPBIOS parport det
ected.
Jul  9 17:36:31 localhost kernel: [17179592.568000] parport0: PC-style at 0x378
(0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Jul  9 17:36:31 localhost kernel: [17179592.572000] parport0 (addr 0): SCSI adap
ter, IMG VP1
Jul  9 17:36:31 localhost kernel: [17179592.684000] e100: eth0: e100_watchdog: l
ink up, 100Mbps, full-duplex
Jul  9 17:36:31 localhost kernel: [17179592.960000] input: ImExPS/2 Generic Expl
orer Mouse as /class/input/input2
Jul  9 17:36:31 localhost kernel: [17179593.012000] ts: Compaq touchscreen proto
col output
Jul  9 17:36:31 localhost kernel: [17179593.416000] lp0: using parport0 (interru
pt-driven).
Jul  9 17:36:31 localhost kernel: [17179593.484000] SCSI subsystem initialized
Jul  9 17:36:31 localhost kernel: [17179593.504000] ppa: Version 2.07 (for Linux
 2.4.x)
Jul  9 17:36:31 localhost kernel: [17179593.556000] Adding 1502036k swap on /dev
/hda5.  Priority:-1 extents:1 across:1502036k
Jul  9 17:36:31 localhost kernel: [17179593.732000] EXT3 FS on hda1, internal jo
urnal
Jul  9 17:36:31 localhost kernel: [17179593.748000] NET: Registered protocol fam
ily 17
Jul  9 17:36:31 localhost kernel: [17179593.932000] md: md driver 0.90.3 MAX_MD_
DEVS=256, MD_SB_DISKS=27
Jul  9 17:36:31 localhost kernel: [17179593.932000] md: bitmap version 4.39
Jul  9 17:36:31 localhost kernel: [17179594.508000] device-mapper: 4.4.0-ioctl (
2005-01-12) initialised: dm-devel@redhat.com
Jul  9 17:36:31 localhost kernel: [17179594.816000] cdrom: open failed.
Jul  9 17:36:31 localhost kernel: [17179595.264000] cdrom: open failed.
Jul  9 17:36:31 localhost kernel: [17179595.304000] cdrom: open failed.
Jul  9 17:36:31 localhost kernel: [17179596.164000] NET: Registered protocol fam
ily 10
Jul  9 17:36:31 localhost kernel: [17179596.164000] lo: Disabled Privacy Extensi
ons
Jul  9 17:36:31 localhost kernel: [17179596.168000] IPv6 over IPv4 tunneling dri
ver
Jul  9 17:36:31 localhost kernel: [17179602.036000] ACPI: Power Button (FF) [PWR
F]
Jul  9 17:36:31 localhost kernel: [17179602.036000] ACPI: Power Button (CM) [VBT
N]
Jul  9 17:36:31 localhost kernel: [17179602.264000] pcc_acpi: loading...
Jul  9 17:36:34 localhost hpiod: 0.9.7 accepting connections at 35899...
Jul  9 17:36:35 localhost kernel: [17179607.512000] [drm] Initialized drm 1.0.1
20051102
Jul  9 17:36:35 localhost kernel: [17179607.536000] ACPI: PCI Interrupt 0000:00:
02.0[A] -> GSI 16 (level, low) -> IRQ 177
Jul  9 17:36:35 localhost kernel: [17179607.536000] [drm] Initialized i915 1.4.0
 20060119 on minor 0
Jul  9 17:36:36 localhost kernel: [17179609.124000] ppdev: user-space parallel p
ort driver
Jul  9 17:36:37 localhost kernel: [17179609.424000] apm: BIOS version 1.2 Flags
0x03 (Driver version 1.16ac)
Jul  9 17:36:37 localhost kernel: [17179609.424000] apm: overridden by ACPI.
Jul  9 17:36:40 localhost kernel: [17179612.844000] Bluetooth: Core ver 2.8
Jul  9 17:36:40 localhost kernel: [17179612.844000] NET: Registered protocol fam
ily 31
Jul  9 17:36:40 localhost kernel: [17179612.844000] Bluetooth: HCI device and co
nnection manager initialized
Jul  9 17:36:40 localhost kernel: [17179612.844000] Bluetooth: HCI socket layer
initialized
Jul  9 17:36:40 localhost kernel: [17179612.900000] Bluetooth: L2CAP ver 2.8
Jul  9 17:36:40 localhost kernel: [17179612.900000] Bluetooth: L2CAP socket laye
r initialized
Jul  9 17:36:40 localhost kernel: [17179612.960000] Bluetooth: RFCOMM socket lay
er initialized
Jul  9 17:36:40 localhost kernel: [17179612.960000] Bluetooth: RFCOMM TTY layer
initialized
Jul  9 17:36:40 localhost kernel: [17179612.960000] Bluetooth: RFCOMM ver 1.7
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): starting (version 2.14.0), pi
d 4790 user 'dajrsmith'
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): Resolved address "xml:readonl
y:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at positio
n 0
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): Resolved address "xml:readwri
te:/home/dajrsmith/.gconf" to a writable configuration source at position 1
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): Resolved address "xml:readonl
y:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position
 2
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): Resolved address "xml:readonl
y:/var/lib/gconf/debian.defaults" to a read-only configuration source at positio
n 3
Jul  9 17:36:54 localhost gconfd (dajrsmith-4790): Resolved address "xml:readonl
y:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  9 17:36:58 localhost gconfd (dajrsmith-4790): Resolved address "xml:readwri
te:/home/dajrsmith/.gconf" to a writable configuration source at position 0

```

Sorry for the delay.  The script premissions wouldn't work for sudo in that command to clear the file.  I had to use this instead:  sudo sh -c 'cat /dev/null > /var/log/messages'

Thanks again!

---

### Post by taurus on 2006-07-09
What's the output of this command then?
```

dmesg | more
(hit space bar for the next 24 lines...)

```

---

### Post by ssmithy on 2006-07-09
```

[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[17179569.184000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 130672
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126576 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
[17179569.184000] ACPI: RSDT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd28b
[17179569.184000] ACPI: FADT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd2bf
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd1b7f
[17179569.184000] ACPI: MADT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd333
[17179569.184000] ACPI: BOOT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd39f
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 2394.617 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.168000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.172000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.180000] Memory: 507700k/522688k available (1976k kernel code, 14408k reserved, 606k data, 288k init, 0k highmem)
[17179573.180000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.260000] Calibrating delay using timer specific routine.. 4793.23 BogoMIPS (lpj=9586468)
[17179573.260000] Security Framework v1.0.0 initialized
[17179573.260000] SELinux:  Disabled at boot.
[17179573.260000] Mount-cache hash table entries: 512
[17179573.260000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179573.260000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179573.260000] monitor/mwait feature present.
[17179573.260000] using mwait in idle threads.
[17179573.260000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179573.260000] CPU: L2 cache: 256K
[17179573.260000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[17179573.260000] mtrr: v2.0 (20020519)
[17179573.260000] CPU: Intel(R) Celeron(R) CPU 2.40GHz stepping 01
[17179573.260000] Enabling fast FPU save and restore... done.
[17179573.260000] Enabling unmasked SIMD FPU exception support... done.
[17179573.260000] Checking 'hlt' instruction... OK.
[17179573.276000] checking if image is initramfs... it is
[17179573.908000] Freeing initrd memory: 6613k freed
[17179573.920000] ACPI: Looking for DSDT ... not found!
[17179573.948000] ENABLING IO-APIC IRQs
[17179573.948000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.092000] NET: Registered protocol family 16
[17179574.092000] EISA bus registered
[17179574.092000] ACPI: bus type pci registered
[17179574.104000] PCI: PCI BIOS revision 2.10 entry at 0xfbbf8, last bus=1
[17179574.104000] PCI: Using configuration type 1
[17179574.104000] ACPI: Subsystem revision 20051216
[17179574.140000] ACPI: Interpreter enabled
[17179574.140000] ACPI: Using IOAPIC for interrupt routing
[17179574.144000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.144000] PCI: Probing PCI hardware (bus 00)
[17179574.148000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.164000] Boot video device is 0000:00:02.0
[17179574.164000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179574.164000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179574.164000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.164000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179574.344000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179574.344000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179574.344000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179574.348000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179574.348000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179574.348000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179574.348000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179574.352000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179574.352000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.352000] pnp: PnP ACPI init
[17179574.384000] pnp: PnP ACPI: found 11 devices
[17179574.384000] PnPBIOS: Disabled by ACPI PNP
[17179574.384000] PCI: Using ACPI for IRQ routing
[17179574.384000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.396000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[17179574.396000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[17179574.396000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[17179574.396000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179574.396000] PCI: Bridge: 0000:00:1e.0
[17179574.396000]   IO window: d000-dfff
[17179574.396000]   MEM window: fea00000-feafffff
[17179574.396000]   PREFETCH window: disabled.
[17179574.396000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.396000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[17179574.396000] Simple Boot Flag at 0x7a set to 0x1
[17179574.396000] audit: initializing netlink socket (disabled)
[17179574.396000] audit(1152484566.396:1): initialized
[17179574.396000] VFS: Disk quotas dquot_6.5.1
[17179574.396000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.396000] Initializing Cryptographic API
[17179574.396000] io scheduler noop registered
[17179574.396000] io scheduler anticipatory registered
[17179574.396000] io scheduler deadline registered
[17179574.396000] io scheduler cfq registered
[17179574.396000] isapnp: Scanning for PnP cards...
[17179574.748000] isapnp: No Plug & Play device found
[17179574.772000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179574.776000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.776000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.776000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.776000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.780000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.780000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.780000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.780000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.780000] mice: PS/2 mouse device common for all mice
[17179574.784000] EISA: Probing bus 0 at eisa.0
[17179574.784000] EISA: Detected 0 cards.
[17179574.784000] NET: Registered protocol family 2
[17179574.812000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.824000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.824000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.824000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.824000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.824000] TCP reno registered
[17179574.824000] TCP bic registered
[17179574.824000] NET: Registered protocol family 1
[17179574.824000] NET: Registered protocol family 8
[17179574.824000] NET: Registered protocol family 20
[17179574.824000] Using IPI Shortcut mode
[17179574.824000] ACPI wakeup devices:
[17179574.824000] VBTN PCI0 USB0 USB1 USB2 USB3 PCI1  KBD
[17179574.824000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.824000] Freeing unused kernel memory: 288k freed
[17179574.876000] vga16fb: initializing
[17179574.876000] vga16fb: mapped to 0xc00a0000
[17179574.996000] Console: switching to colour frame buffer device 80x25
[17179574.996000] fb0: VGA16 VGA frame buffer device
[17179576.092000] Capability LSM initialized
[17179576.808000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179576.808000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179576.808000] ICH5: chipset revision 2
[17179576.808000] ICH5: not 100% native mode: will probe irqs later
[17179576.808000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179576.808000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179576.808000] Probing IDE interface ide0...
[17179577.096000] hda: SAMSUNG SP0802N, ATA DISK drive
[17179577.768000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.772000] Probing IDE interface ide1...
[17179578.508000] hdc: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
[17179578.956000] hdd: SONY CD-RW CRX216E, ATAPI CD/DVD-ROM drive
[17179579.012000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.024000] hda: max request size: 1024KiB
[17179579.040000] hda: Host Protected Area detected.
[17179579.040000]       current capacity is 156250000 sectors (80000 MB)
[17179579.040000]       native  capacity is 156368016 sectors (80060 MB)
[17179579.040000] hda: Host Protected Area disabled.
[17179579.040000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.040000] hda: cache flushes supported
[17179579.040000]  hda: hda1 hda2 < hda5 >
[17179579.080000] hdc: ATAPI 48X DVD-ROM drive, 254kB Cache, UDMA(33)
[17179579.080000] Uniform CD-ROM driver Revision: 3.20
[17179579.096000] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.280000] usbcore: registered new driver usbfs
[17179579.280000] usbcore: registered new driver hub
[17179579.280000] USB Universal Host Controller Interface driver v2.3
[17179579.280000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179579.280000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.280000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.280000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.280000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000ff80
[17179579.280000] hub 1-0:1.0: USB hub found
[17179579.280000] hub 1-0:1.0: 2 ports detected
[17179579.384000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179579.384000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.384000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.384000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.384000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000ff60
[17179579.384000] hub 2-0:1.0: USB hub found
[17179579.384000] hub 2-0:1.0: 2 ports detected
[17179579.488000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17179579.488000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179579.488000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179579.488000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[17179579.488000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ff20
[17179579.488000] hub 3-0:1.0: USB hub found
[17179579.488000] hub 3-0:1.0: 2 ports detected
[17179579.592000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179579.592000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.592000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.592000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.592000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.592000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179579.592000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffa80800
[17179579.596000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.596000] hub 4-0:1.0: USB hub found
[17179579.596000] hub 4-0:1.0: 8 ports detected
[17179579.824000] Attempting manual resume
[17179579.892000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.892000] kjournald starting.  Commit interval 5 seconds
[17179591.348000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.352000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.380000] hw_random hardware driver 1.0.0 loaded
[17179591.452000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.456000] agpgart: Detected an Intel 865 Chipset.
[17179591.456000] agpgart: Detected 892K stolen memory.
[17179591.472000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179591.900000] input: PC Speaker as /class/input/input1
[17179592.052000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179592.052000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179592.124000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179592.124000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179592.280000] Floppy drive(s): fd0 is 1.44M
[17179592.296000] FDC 0 is a post-1991 82077
[17179592.372000] intel8x0_measure_ac97_clock: measured 55589 usecs
[17179592.372000] intel8x0: clocking to 48000
[17179592.372000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179592.392000] e100: eth0: e100_probe: addr 0xfeaef000, irq 209, MAC addr 00:13:20:46:D6:40
[17179592.500000] Real Time Clock Driver v1.12
[17179592.568000] parport: PnPBIOS parport detected.
[17179592.568000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179592.572000] parport0: device reported incorrect length field (61, should be 62)
[17179592.572000] parport0 (addr 0): SCSI adapter, IMG VP1
[17179592.684000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179592.960000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179593.012000] ts: Compaq touchscreen protocol output
[17179593.416000] lp0: using parport0 (interrupt-driven).
[17179593.484000] SCSI subsystem initialized
[17179593.504000] ppa: Version 2.07 (for Linux 2.4.x)
[17179593.556000] Adding 1502036k swap on /dev/hda5.  Priority:-1 extents:1 across:1502036k
[17179593.732000] EXT3 FS on hda1, internal journal
[17179593.748000] NET: Registered protocol family 17
[17179593.932000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.932000] md: bitmap version 4.39
[17179594.508000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179594.816000] cdrom: open failed.
[17179595.264000] cdrom: open failed.
[17179595.304000] cdrom: open failed.
[17179596.164000] NET: Registered protocol family 10
[17179596.164000] lo: Disabled Privacy Extensions
[17179596.168000] IPv6 over IPv4 tunneling driver
[17179602.036000] ACPI: Power Button (FF) [PWRF]
[17179602.036000] ACPI: Power Button (CM) [VBTN]
[17179602.224000] ibm_acpi: ec object not found
[17179602.264000] pcc_acpi: loading...
[17179606.700000] eth0: no IPv6 routers present
[17179607.512000] [drm] Initialized drm 1.0.1 20051102
[17179607.536000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179607.536000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179609.124000] ppdev: user-space parallel port driver
[17179609.424000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179609.424000] apm: overridden by ACPI.
[17179612.844000] Bluetooth: Core ver 2.8
[17179612.844000] NET: Registered protocol family 31
[17179612.844000] Bluetooth: HCI device and connection manager initialized
[17179612.844000] Bluetooth: HCI socket layer initialized
[17179612.900000] Bluetooth: L2CAP ver 2.8
[17179612.900000] Bluetooth: L2CAP socket layer initialized
[17179612.960000] Bluetooth: RFCOMM socket layer initialized
[17179612.960000] Bluetooth: RFCOMM TTY layer initialized
[17179612.960000] Bluetooth: RFCOMM ver 1.7

```

---

### Post by ssmithy on 2006-07-09
I also just tried changing the file permissions 770, 700, 744, 444, etc. on the zip drive.  That seemed to have little effect. :(

Let me know if you can think of anything else.

---

### Post by taurus on 2006-07-09
I don't see anywhere in dmesg that says about your paralell zip drive!  I assume you have it plug in, turn on, and with a media inside!

p.s.  It has nothing to do with permissions at this point.

---

### Post by ssmithy on 2006-07-09
For the benefit of the doubt, I checked all the connections and rebooted.  It lists the device, but will not mount.  I can even right click the icon, go to properties, and see how large the disk is.

---

### Post by taurus on 2006-07-09
Well, you can always try /dev/sda1, /dev/sda2, or /dev/sda3 since /dev/sda4 doesn't work!!!

---

### Post by ssmithy on 2006-07-09
I tried that.  

mount: special device /dev/sda(1,2,3, and 4) does not exist

---

### Post by ssmithy on 2006-07-09
Here's my fstab file to show how it tries to mount:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0

```

Maybe this is configured incorrectly?

---

### Post by ssmithy on 2006-07-09
Still no luck.  I'm giving up for the night and I'll try to spend some time on this tomorrow.  If anyone can think of a reason on why the sda is not showing up in my dmesg or /var/log/messages please let me know.
Thanks!

---

### Post by ssmithy on 2006-07-11
Alright, I did a little more poking around on the debian forums.  I couldn't really find anything new.  I did try installing the zip drive on my Dapper computer, instead of my fathers.  Unfortunately, I got the same error message when mounting the drive.  So, now I'm wondering if the problem is with Ubuntu 6.06?  If anyone has any tips or ideas please let me know.  I'm not ready to give up on this yet.  If I can get this drive up and running, my dad will be quite happy! ;)

---

### Post by ssmithy on 2006-07-12
After fiddling with this some more I am wondering if I need to compile a custom kernel that includes SCSI support.  So, I am wondering is there an easy way to tell if my kernel has SCSI support loaded.  

This all seems wierd.  I know that parallel SCSI drives are kinda old but I figured Dapper would support these.  

Any help?  :???:

---

### Post by ssmithy on 2006-07-12
I got it to work!  I needed to use the imm module instead of ppa.  Apparently this zip is newer than I thought.  I ran modprobe imm and my zip drive worked!

Thanks taurus for the help!  I'm glad I didn't give up. :)

---

