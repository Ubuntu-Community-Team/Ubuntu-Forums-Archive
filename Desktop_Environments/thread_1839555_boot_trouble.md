---
title: "boot trouble"
date: 2011-09-05
forum: Desktop Environments
---

### Post by GlennW on 2011-09-05
I've got an issue I have no idea how to solve. The other day I was watching a movie on xbmc on my 64 bit ubuntu 11.04 desktop box. I wasn't going to be home the following couple of days so I shut the box down. Upon starting up yesterday, it seemed to be a normal boot up but it stopped/hung up at the purple screen. I rebooted a couple times with the same result. I selected recovery mode which ended up kicking me to the command line almost immediately. I entered <startx> and the desktop was loaded albeit without the upper and lower panel menus. After some searching (using my laptop) I found that if I used the command <gnome-terminal --replace> in the terminal (ctrl+alt+t) the panels returned. However, this is only a temporary fix. If I close the terminal then the panel menus also disappear. Rebooting still doesn't correct the problem. 

Does anyone have some insight into this issue?

---

### Post by GlennW on 2011-09-06
Anyone?

---

### Post by raja.genupula on 2011-09-07
are you able to login from terminal 

then stop your gdm and start it again 

 ```
sudo /etc/init.d/gdm stop
```

 ```
sudo /etc/init.d/gdm start
```

let us know what you got ?

---

### Post by GlennW on 2011-09-07
> **raja.genupula said:**
> are you able to login from terminal 

then stop your gdm and start it again 

 ```
sudo /etc/init.d/gdm stop
```

 ```
sudo /etc/init.d/gdm start
```

let us know what you got ?

I copied your stop command into terminal and the result was command not found.

Thanks for your time on this.

---

### Post by raja.genupula on 2011-09-07
what ? 
its impossible , i have given this suggestion to many people 
they have not got any thing like . could you please do it again , careful about each letter .

---

### Post by GlennW on 2011-09-07
> **raja.genupula said:**
> what ? 
its impossible , i have given this suggestion to many people 
they have not got any thing like . could you please do it again , careful about each letter .

The way that I began this x session was to try and boot from recovery mode. I then choose to continue the boot procedure using the safe graphics mode or whatever its wording was. Instead of bringing me to a pared down graphics desktop, it kicked me to the command line. I entered startx. That got me to my desktop and compiz running but no gnome panels. I had hunted through some forums and found the command gnome-panel --replace. That restored, from what I can tell, full functionality except that if I close the terminal I loose gnome. 

I did enter your command string (copy and paste) again with this terminal output: /etc/init.d/gdm: command not found.

I did this several times to make sure that the syntax was correct.

Does this have anything to do a grub corruption? Just guessing....

---

### Post by wildmanne39 on 2011-09-08
Hi, you are getting past the grub from what you say, you probably had an update to your video card driver, try nomodeset options to see if it will let you boot so you can fix your system, here is a link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by stinkeye on 2011-09-08
> **raja.genupula said:**
> what ? 
its impossible , i have given this suggestion to many people 
they have not got any thing like . could you please do it again , careful about each letter .

For Natty use
```
sudo service gdm restart
```

---

### Post by raja.genupula on 2011-09-08
> **stinkeye said:**
> For Natty use
```
sudo service gdm restart
```


thank you , i will update it .

---

### Post by GlennW on 2011-09-08
> **stinkeye said:**
> For Natty use
```
sudo service gdm restart
```

That command produces this terminal output: restart: Unknown instance:

I then altered it to sudo service gdm start with this output: gdm stop/waiting and the panels disappearing. 

The only way, at this point, that I can restore them is with gnome-panel --replace

This is frustrating to say the least.

I should add that I can't boot off of a live 11.04 usb drive. I've checked the usb drive in my laptop and it boots fine from it. 

Thanks.

---

### Post by stinkeye on 2011-09-08
You can just put
```
gnome-panel
```
in startup applications as a quick fix.

---

### Post by GlennW on 2011-09-09
> **stinkeye said:**
> You can just put
```
gnome-panel
```
in startup applications as a quick fix.

Nope. That just causes x to crash. Earlier my wife had shut the box down. I went through the same start sequence as I had before:

latest kernel recovery mode
run in graphics fail safe mode (kicks me to black screen with command line)
startx (desktop follows but without gnome panels)
in terminal run gnome-panel --replace

However, this last time, after choosing run in graphics fail safe mode, there was a bunch of code scrolling up the screen and then it stopped at grub-editenv: error: cannot open the file /boot/grub/grubenv

I rebooted and, on a lark, scrolled down and chose the second kernel option 2.6.32-25. That launched without a hitch. After a couple of seconds I realized that it had mounted the smaller hdd and not my primary 1 TB drive.

So, by now I am so thoroughly confused and frustrated I don't know what to do. I do, however, still think it's a grub/boot issue especially after the aforementioned grub error message.

---

### Post by wildmanne39 on 2011-09-09
Hi, did you install upgrades like for video card or the kernel just before this happened? 

Did you try what I posted in post 7?

It sounds like there may be a different issue now also.

A long time ago I did an upgrade and I was never able to get the upgraded kernel to work but that was before I learned a few things.

If you can get back into recovery run these commands and it should tell us what is going on.
```
dmesg |tail -n300
```
```
tail -n300 /var/log/syslog
```
```
tail -n300 /var/log/kern.log
```
Thank you

---

### Post by GlennW on 2011-09-10
> **wildmanne39 said:**
> Hi, did you install upgrades like for video card or the kernel just before this happened? 

Did you try what I posted in post 7?

It sounds like there may be a different issue now also.

A long time ago I did an upgrade and I was never able to get the upgraded kernel to work but that was before I learned a few things.

If you can get back into recovery run these commands and it should tell us what is going on.
```
dmesg |tail -n300
```
```
tail -n300 /var/log/syslog
```
```
tail -n300 /var/log/kern.log
```
Thank you

I've tried to get back to the command line but I can only get as far as the root shell with networking. Following are the outputs for each of the three commands you suggest.

For dmesg |tail -n300
```
root@glenn-desktop:~# dmesg |tail -n300
[    0.399967] TCP reno registered
[    0.399967] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.399967] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.399967] NET: Registered protocol family 1
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0b.0: Linking AER extended capability
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0c.0: Linking AER extended capability
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0d.0: Linking AER extended capability
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.399967] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.399967] pci 0000:00:0e.0: Linking AER extended capability
[    0.399967] pci 0000:05:00.0: Boot video device
[    0.399967] PCI: CLS 32 bytes, default 64
[    0.510661] audit: initializing netlink socket (disabled)
[    0.510723] type=2000 audit(1315593857.509:1): initialized
[    0.525833] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.527934] VFS: Disk quotas dquot_6.5.2
[    0.528046] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.528860] fuse init (API version 7.16)
[    0.529014] msgmni has been set to 3987
[    0.529361] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.529446] io scheduler noop registered
[    0.529492] io scheduler deadline registered
[    0.529582] io scheduler cfq registered (default)
[    0.529852] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.529891] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.530049] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.530072] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    0.540247] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.540282] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    0.540402] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.540421] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    0.540510] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.540583] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.540821] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.540883] ACPI: Power Button [PWRB]
[    0.540995] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.541052] ACPI: Power Button [PWRF]
[    0.541419] ACPI: acpi_idle registered with cpuidle
[    0.543465] ERST: Table is not found!
[    0.543624] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.564172] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.576887] Freeing initrd memory: 12876k freed
[    0.630443] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.990605] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.990998] Linux agpgart interface v0.103
[    0.992386] brd: module loaded
[    0.993029] loop: module loaded
[    0.993230] i2c-core: driver [adp5520] using legacy suspend method
[    0.993277] i2c-core: driver [adp5520] using legacy resume method
[    0.993654] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.993969] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.994035] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.994126] pata_acpi 0000:00:07.0: setting latency timer to 64
[    0.994134] pata_acpi 0000:00:07.0: PCI INT A disabled
[    0.994417] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.994472] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.994548] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.994556] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.995165] Fixed MDIO Bus: probed
[    0.995251] PPP generic driver version 2.4.2
[    0.995354] tun: Universal TUN/TAP device driver, 1.6
[    0.995401] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.995556] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.995767] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.995823] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.995895] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.995898] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.996028] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.030055] ehci_hcd 0000:00:02.1: debug port 1
[    1.030105] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    1.030127] ehci_hcd 0000:00:02.1: irq 21, io mem 0x80100000
[    1.050026] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.050215] hub 1-0:1.0: USB hub found
[    1.050264] hub 1-0:1.0: 10 ports detected
[    1.050416] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.050650] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    1.050712] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    1.050781] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.050784] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.050879] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.090049] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf5002000
[    1.152174] hub 2-0:1.0: USB hub found
[    1.152223] hub 2-0:1.0: 10 ports detected
[    1.152365] uhci_hcd: USB Universal Host Controller Interface driver
[    1.152550] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.152598] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.153462] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.154320] mousedev: PS/2 mouse device common for all mice
[    1.154503] rtc_cmos 00:04: RTC can wake from S4
[    1.174997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.190083] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.190154] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    1.190317] device-mapper: uevent: version 1.0.3
[    1.190459] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.190626] device-mapper: multipath: version 1.2.0 loaded
[    1.190675] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.190878] cpuidle: using governor ladder
[    1.190926] cpuidle: using governor menu
[    1.191304] TCP cubic registered
[    1.191486] NET: Registered protocol family 10
[    1.192069] NET: Registered protocol family 17
[    1.192136] Registering the dns_resolver key type
[    1.192212] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 cpu cores) (version 2.20.00)
[    1.192329] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    1.192376] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    1.192596] PM: Hibernation image not present or could not be loaded.
[    1.192617] registered taskstats version 1
[    1.192912]   Magic number: 11:288:746
[    1.192992] pci_express 0000:00:0d.0:pcie08: hash matches
[    1.193132] rtc_cmos 00:04: setting system clock to 2011-09-09 18:44:18 UTC (1315593858)
[    1.193189] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.193236] EDD information not available.
[    1.195215] Freeing unused kernel memory: 956k freed
[    1.195833] Write protecting the kernel read-only data: 10240k
[    1.196711] Freeing unused kernel memory: 184k freed
[    1.202247] Freeing unused kernel memory: 1440k freed
[    1.228074] <30>udev[98]: starting version 167
[    1.296881] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.297181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.297235] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.297296] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.362652] via-rhine.c:v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.370100] usb 1-7: new high speed USB device using ehci_hcd and address 2
[    1.371742] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    1.371819] via-rhine 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    1.376291] eth0: VIA Rhine II at 0xf4005000, 00:50:ba:1b:ce:f6, IRQ 16.
[    1.377045] eth0: MII PHY found at address 8, status 0x782d advertising 01e1 Link 4de1.
[    1.380923] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    1.380996] firewire_ohci 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    1.440091] firewire_ohci: Added fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.821025] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x3f1 @ 7, addr 00:14:85:10:f2:18
[    1.821088] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    1.821602] pata_amd 0000:00:06.0: version 0.4.1
[    1.821656] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.822233] scsi0 : pata_amd
[    1.822609] scsi1 : pata_amd
[    1.823134] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.823183] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.823443] sata_nv 0000:00:07.0: version 3.5
[    1.823458] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.823574] sata_nv 0000:00:07.0: setting latency timer to 64
[    1.823876] scsi2 : sata_nv
[    1.824018] scsi3 : sata_nv
[    1.824193] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xcc00 irq 23
[    1.824242] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xcc08 irq 23
[    1.824384] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.824490] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.824762] scsi4 : sata_nv
[    1.824903] scsi5 : sata_nv
[    1.825064] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe000 irq 22
[    1.825114] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe008 irq 22
[    1.860063] usb 1-9: new high speed USB device using ehci_hcd and address 4
[    1.940153] firewire_core: created device fw0: GUID 00148556000f37dc, S800
[    2.000381] ata1.00: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[    2.000432] ata1.00: 156301488 sectors, multi 16: LBA 
[    2.000487] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    2.019249] usbcore: registered new interface driver uas
[    2.020355] ata1.00: configured for UDMA/100
[    2.020606] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[    2.020881] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.020923] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.020973] sd 0:0:0:0: [sda] Write Protect is off
[    2.020976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.020998] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.049862]  sda: sda1 sda2 < sda5 >
[    2.050432] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.130029] usb 1-10: new high speed USB device using ehci_hcd and address 5
[    2.150083] ata5: SATA link down (SStatus 0 SControl 300)
[    2.220272] ata2.00: ATAPI: HITACHI GD-2000, 0056, max MWDMA2
[    2.220324] ata2.01: ATAPI: HL-DT-ST GCE-8400B, 1.02, max MWDMA2
[    2.220378] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:120:0x1a)
[    2.220383] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:120:0x1a)
[    2.260204] ata2.00: configured for MWDMA2
[    2.293285] Initializing USB Mass Storage driver...
[    2.293553] scsi6 : usb-storage 1-9:1.3
[    2.293841] scsi7 : usb-storage 1-10:1.0
[    2.294013] usbcore: registered new interface driver usb-storage
[    2.294062] USB Mass Storage support registered.
[    2.300235] ata2.01: configured for MWDMA2
[    2.310039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.330301] ata3.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    2.330350] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.330836] scsi 1:0:0:0: CD-ROM            HITACHI  GD-2000          0056 PQ: 0 ANSI: 5
[    2.361111] sr0: scsi3-mmc drive: 8x/20x cd/rw xa/form2 cdda tray
[    2.361160] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.361369] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.361475] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.361868] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  1.02 PQ: 0 ANSI: 5
[    2.370321] ata3.00: configured for UDMA/133
[    2.372919] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.373078] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.373148] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.373389] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    2.373641] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    2.373791] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.373917] sd 2:0:0:0: [sdb] Write Protect is off
[    2.373965] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.373988] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.415132]  sdb: sdb1 sdb2 < sdb5 >
[    2.415532] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.620075] usb 2-8: new low speed USB device using ohci_hcd and address 2
[    2.700034] ata4: SATA link down (SStatus 0 SControl 300)
[    2.910136] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-8/2-8:1.0/input/input3
[    2.910329] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-8/input0
[    2.920657] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-8/2-8:1.1/input/input4
[    2.920839] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-8/input1
[    2.920918] usbcore: registered new interface driver usbhid
[    2.920966] usbhid: USB HID core driver
[    3.030024] ata6: SATA link down (SStatus 0 SControl 300)
[    3.292480] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[    3.293937] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    3.294152] scsi 7:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
[    3.296848] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    3.300303] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    3.302855] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    3.384639] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    5.591998] Adding 2096124k swap on /dev/sdb5.  Priority:-1 extents:1 across:2096124k 
[    6.211969] <30>udev[417]: starting version 167
[    8.646152] nvidia: module license 'NVIDIA' taints kernel.
[    8.646158] Disabling lock debugging due to kernel taint
[    9.255175] MCE: In-kernel MCE decoding enabled.
[    9.260425] parport_pc 00:09: reported by Plug and Play ACPI
[    9.260470] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.296145] ppdev: user-space parallel port driver
[    9.484089] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    9.484104] nvidia 0000:05:00.0: setting latency timer to 64
[    9.484111] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.485183] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[    9.515267] EDAC MC: Ver: 2.1.0 Aug 29 2011
[    9.588023] Linux video capture interface: v2.00
[    9.607590] EDAC amd64_edac: v3.3.0
[    9.607763] EDAC amd64: DRAM ECC disabled.
[    9.607777] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    9.607778]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    9.607780]  (Note that use of the override may cause unknown side effects.)
[    9.673108] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)
[    9.689210] input: UVC Camera (046d:08c9) as /devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/input/input5
[    9.689345] usbcore: registered new interface driver uvcvideo
[    9.689348] USB Video Class driver (v1.0.0)
[    9.700091] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    9.700146] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[    9.726103] lp0: using parport0 (interrupt-driven).
[   10.104974] type=1400 audit(1315593867.397:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=633 comm="apparmor_parser"
[   10.105357] type=1400 audit(1315593867.397:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
[   10.105603] type=1400 audit(1315593867.397:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
[   10.106282] type=1400 audit(1315593867.397:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
[   10.106662] type=1400 audit(1315593867.397:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
[   10.106910] type=1400 audit(1315593867.397:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
[   10.107618] type=1400 audit(1315593867.397:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=807 comm="apparmor_parser"
[   10.108002] type=1400 audit(1315593867.397:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
[   10.108260] type=1400 audit(1315593867.397:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
[   10.112415] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   10.112423] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   10.112455] Intel ICH 0000:00:04.0: setting latency timer to 64
[   10.321882] usbcore: registered new interface driver snd-usb-audio
[   10.429879] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[   10.430342] usbcore: registered new interface driver usblp
[   10.450037] intel8x0_measure_ac97_clock: measured 50048 usecs (2464 samples)
[   10.450042] intel8x0: clocking to 46798
[   10.495992] type=1400 audit(1315593867.787:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=899 comm="apparmor_parser"
[   46.721343] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   47.712574] audit_printk_skb: 6 callbacks suppressed
[   47.712579] type=1400 audit(1315593905.016:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1024 comm="apparmor_parser"
[   47.712985] type=1400 audit(1315593905.016:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1024 comm="apparmor_parser"
[   47.713236] type=1400 audit(1315593905.016:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1024 comm="apparmor_parser"
[   47.846923] type=1400 audit(1315593905.146:17): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1023 comm="apparmor_parser"
[   47.945050] type=1400 audit(1315593905.246:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1039 comm="apparmor_parser"
[   47.945077] type=1400 audit(1315593905.246:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1045 comm="apparmor_parser"
[   47.945524] type=1400 audit(1315593905.246:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1039 comm="apparmor_parser"
[   47.945562] type=1400 audit(1315593905.246:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1045 comm="apparmor_parser"
[   48.297968] type=1400 audit(1315593905.596:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1025 comm="apparmor_parser"
[   48.303152] type=1400 audit(1315593905.606:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1025 comm="apparmor_parser"
[   49.180958] eth0: link up, 100Mbps, full-duplex, lpa 0x4DE1
[   49.271954] forcedeth 0000:00:0a.0: eth1: no link during initialization
[   49.272714] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   50.124278] usb 1-9: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   59.330020] eth0: no IPv6 routers present
[  631.175743] mtrr: no MTRR for e0000000,10000000 found
[  676.530463] show_signal_msg: 12 callbacks suppressed
[  676.530469] compiz[2227]: segfault at 0 ip 0000000040035fa8 sp 00007ffff45114c8 error 4 in glVu7zYr (deleted)[40034000+2000]
[  677.166095] compiz[2283]: segfault at 0 ip 0000000041b40fa8 sp 00007fff9343efd8 error 4 in gldtYlM5 (deleted)[41b3f000+2000]
[  677.880114] compiz[2304]: segfault at 0 ip 0000000041ad7fa8 sp 00007fff43fbaad8 error 4 in glBVDrDK (deleted)[41ad6000+2000]
[  679.092149] compiz[2332]: segfault at 0 ip 0000000041175fa8 sp 00007fffb8709078 error 4 in glvI2m94 (deleted)[41174000+2000]
[  679.966920] compiz[2397]: segfault at 0 ip 00000000407dcfa8 sp 00007fff32565968 error 4 in glNQiw4X (deleted)[407db000+2000]
[  680.773312] compiz[2409]: segfault at 0 ip 0000000040775fa8 sp 00007fffcdddafc8 error 4 in glBCPpkM (deleted)[40774000+2000]
[  680.858408] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[  681.800248] compiz[2424]: segfault at 0 ip 0000000041c58fa8 sp 00007fffd1560238 error 4 in gliDNF0Q (deleted)[41c57000+2000]
[ 3013.870110] unity-window-de[2280]: segfault at ffffffff ip 00007fc3477492b6 sp 00007fffc7fc48a0 error 4 in libglib-2.0.so.0.2800.6[7fc3476e9000+ed000]
[ 3026.701551] unity-window-de[2777]: segfault at ffffffff ip 00007fc8516bd2b6 sp 00007fffdbd231d0 error 4 in libglib-2.0.so.0.2800.6[7fc85165d000+ed000]
[ 3032.724153] unity-window-de[2782]: segfault at ffffffff ip 00007f86aaa492b6 sp 00007fff118d7a50 error 4 in libglib-2.0.so.0.2800.6[7f86aa9e9000+ed000]
```

For tail -n300 /var/log/syslog
```
Sep  9 13:45:04 glenn-desktop kernel: [    9.260425] parport_pc 00:09: reported by Plug and Play ACPI
Sep  9 13:45:04 glenn-desktop kernel: [    9.260470] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep  9 13:45:04 glenn-desktop kernel: [    9.296145] ppdev: user-space parallel port driver
Sep  9 13:45:04 glenn-desktop kernel: [    9.484089] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Sep  9 13:45:04 glenn-desktop kernel: [    9.484104] nvidia 0000:05:00.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    9.484111] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep  9 13:45:04 glenn-desktop kernel: [    9.485183] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Sep  9 13:45:04 glenn-desktop kernel: [    9.515267] EDAC MC: Ver: 2.1.0 Aug 29 2011
Sep  9 13:45:04 glenn-desktop kernel: [    9.588023] Linux video capture interface: v2.00
Sep  9 13:45:04 glenn-desktop kernel: [    9.607590] EDAC amd64_edac: v3.3.0
Sep  9 13:45:04 glenn-desktop kernel: [    9.607763] EDAC amd64: DRAM ECC disabled.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607777] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607778]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607780]  (Note that use of the override may cause unknown side effects.)
Sep  9 13:45:04 glenn-desktop kernel: [    9.673108] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)
Sep  9 13:45:04 glenn-desktop kernel: [    9.689210] input: UVC Camera (046d:08c9) as /devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/input/input5
Sep  9 13:45:04 glenn-desktop kernel: [    9.689345] usbcore: registered new interface driver uvcvideo
Sep  9 13:45:04 glenn-desktop kernel: [    9.689348] USB Video Class driver (v1.0.0)
Sep  9 13:45:04 glenn-desktop kernel: [    9.700091] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Sep  9 13:45:04 glenn-desktop kernel: [    9.700146] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
Sep  9 13:45:04 glenn-desktop kernel: [    9.726103] lp0: using parport0 (interrupt-driven).
Sep  9 13:45:04 glenn-desktop kernel: [   10.104974] type=1400 audit(1315593867.397:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.105357] type=1400 audit(1315593867.397:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.105603] type=1400 audit(1315593867.397:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106282] type=1400 audit(1315593867.397:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106662] type=1400 audit(1315593867.397:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106910] type=1400 audit(1315593867.397:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.107618] type=1400 audit(1315593867.397:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.108002] type=1400 audit(1315593867.397:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.108260] type=1400 audit(1315593867.397:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.112415] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [   10.112423] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [   10.112455] Intel ICH 0000:00:04.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [   10.321882] usbcore: registered new interface driver snd-usb-audio
Sep  9 13:45:04 glenn-desktop kernel: [   10.429879] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
Sep  9 13:45:04 glenn-desktop kernel: [   10.430342] usbcore: registered new interface driver usblp
Sep  9 13:45:04 glenn-desktop kernel: [   10.450037] intel8x0_measure_ac97_clock: measured 50048 usecs (2464 samples)
Sep  9 13:45:04 glenn-desktop kernel: [   10.450042] intel8x0: clocking to 46798
Sep  9 13:45:04 glenn-desktop kernel: [   10.495992] type=1400 audit(1315593867.787:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=899 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   46.721343] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Sep  9 13:45:05 glenn-desktop kernel: [   47.712574] audit_printk_skb: 6 callbacks suppressed
Sep  9 13:45:05 glenn-desktop kernel: [   47.712579] type=1400 audit(1315593905.016:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.712985] type=1400 audit(1315593905.016:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.713236] type=1400 audit(1315593905.016:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.846923] type=1400 audit(1315593905.146:17): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1023 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop init: gdm main process (1046) killed by TERM signal
Sep  9 13:45:05 glenn-desktop kernel: [   47.945050] type=1400 audit(1315593905.246:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1039 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945077] type=1400 audit(1315593905.246:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1045 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945524] type=1400 audit(1315593905.246:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1039 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945562] type=1400 audit(1315593905.246:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1045 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Successfully dropped root privileges.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: avahi-daemon 0.6.30 starting up.
Sep  9 13:45:05 glenn-desktop kernel: [   48.297968] type=1400 audit(1315593905.596:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1025 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   48.303152] type=1400 audit(1315593905.606:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1025 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Successfully called chroot().
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Successfully dropped remaining capabilities.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Loading service file /services/udisks.service.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Network interface enumeration completed.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Server startup complete. Host name is glenn-desktop.local. Local service cookie is 4108457374.
Sep  9 13:45:05 glenn-desktop avahi-daemon[1062]: Service "glenn-desktop" (/services/udisks.service) successfully established.
Sep  9 13:45:05 glenn-desktop NetworkManager[1066]: <info> NetworkManager (version 0.8.3.998) is starting...
Sep  9 13:45:05 glenn-desktop NetworkManager[1066]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> trying to start the modem manager...
Sep  9 13:45:06 glenn-desktop init: rc-sysinit main process (978) killed by TERM signal
Sep  9 13:45:06 glenn-desktop init: ssh main process (986) terminated with status 255
Sep  9 13:45:06 glenn-desktop init: plymouth-stop pre-start process (1113) terminated with status 1
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  ModemManager (version 0.4) starting...
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Longcheer
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Novatel
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin ZTE
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin MotoC
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin AnyData
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Gobi
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Option High-Speed
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Option
Sep  9 13:45:06 glenn-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-9/1-9:1.1
Sep  9 13:45:06 glenn-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-9
Sep  9 13:45:06 glenn-desktop udev-configure-printer: Device vendor/product is 03F0:5711
Sep  9 13:45:06 glenn-desktop udev-configure-printer: failed to claim interface
Sep  9 13:45:06 glenn-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Sep  9 13:45:06 glenn-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-9/1-9:1.1/usb/lp0
Sep  9 13:45:06 glenn-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-9
Sep  9 13:45:06 glenn-desktop udev-configure-printer: MFG:HP MDL:Photosmart C4100 series SERN:MY65CB11GY04J7 serial:MY65CB11GY04J7
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Nokia
Sep  9 13:45:06 glenn-desktop polkitd[1103]: started daemon version 0.101 using authority implementation `local' version `0.101'
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Ericsson MBM
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: init!
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: update_system_hostname
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPluginIfupdown: management mode: unmanaged
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:01:08.0/net/eth0, iface: eth0)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth1, iface: eth1)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth1, iface: eth1): no ifupdown configuration found.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: end _init.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Generic
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Linktop
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    Ifupdown: get unmanaged devices count: 0
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: (19079520) ... get_connections.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    SCPlugin-Ifupdown: (19079520) ... get_connections (managed=false): return empty list.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]:    Ifupdown: get unmanaged devices count: 0
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin X22X
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Networking is enabled by state file
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): carrier is OFF
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): new Ethernet device (driver: 'via-rhine' ifindex: 2)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): now managed
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin SimTech
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Huawei
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): bringing up device.
Sep  9 13:45:06 glenn-desktop modem-manager[1100]: <info>  Loaded plugin Sierra
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): preparing device.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): deactivating device (reason: 2).
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:09.0/0000:01:08.0/net/eth0
Sep  9 13:45:06 glenn-desktop kernel: [   49.180958] eth0: link up, 100Mbps, full-duplex, lpa 0x4DE1
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): carrier is OFF
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): new Ethernet device (driver: 'forcedeth' ifindex: 3)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): now managed
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): bringing up device.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): preparing device.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth1): deactivating device (reason: 2).
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:0a.0/net/eth1
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): carrier now ON (device state 2)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> modem-manager is now available
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Trying to start the supplicant...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  9 13:45:06 glenn-desktop kernel: [   49.271954] forcedeth 0000:00:0a.0: eth1: no link during initialization
Sep  9 13:45:06 glenn-desktop kernel: [   49.272714] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> dhclient started with pid 1186
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  9 13:45:06 glenn-desktop dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep  9 13:45:06 glenn-desktop dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep  9 13:45:06 glenn-desktop dhclient: All rights reserved.
Sep  9 13:45:06 glenn-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  9 13:45:06 glenn-desktop dhclient: 
Sep  9 13:45:06 glenn-desktop NetworkManager[1066]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep  9 13:45:06 glenn-desktop dhclient: Listening on LPF/eth0/00:50:ba:1b:ce:f6
Sep  9 13:45:06 glenn-desktop dhclient: Sending on   LPF/eth0/00:50:ba:1b:ce:f6
Sep  9 13:45:06 glenn-desktop dhclient: Sending on   Socket/fallback
Sep  9 13:45:06 glenn-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  9 13:45:06 glenn-desktop dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Sep  9 13:45:06 glenn-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Sep  9 13:45:07 glenn-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info>   address 192.168.1.2
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info>   prefix 24 (255.255.255.0)
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info>   gateway 192.168.1.1
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info>   nameserver '192.168.1.1'
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Scheduling stage 5
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Done scheduling stage 5
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  9 13:45:07 glenn-desktop dhclient: bound to 192.168.1.2 -- renewal in 35758 seconds.
Sep  9 13:45:07 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: New relevant interface eth0.IPv4 for mDNS.
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Sep  9 13:45:07 glenn-desktop kernel: [   50.124278] usb 1-9: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Sep  9 13:45:07 glenn-desktop hp[1325]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:baff:fe1b:cef6.
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: New relevant interface eth0.IPv6 for mDNS.
Sep  9 13:45:07 glenn-desktop avahi-daemon[1062]: Registering new address record for fe80::250:baff:fe1b:cef6 on eth0.*.
Sep  9 13:45:08 glenn-desktop NetworkManager[1066]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep  9 13:45:08 glenn-desktop NetworkManager[1066]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  9 13:45:08 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) successful, device activated.
Sep  9 13:45:08 glenn-desktop NetworkManager[1066]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  9 13:45:08 glenn-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep  9 13:45:08 glenn-desktop udev-configure-printer: SERN fields match
Sep  9 13:45:08 glenn-desktop udev-configure-printer: URI match: usb://HP/Photosmart%20C4100%20series?serial=MY65CB11GY04J7
Sep  9 13:45:08 glenn-desktop udev-configure-printer: SERN fields match
Sep  9 13:45:08 glenn-desktop udev-configure-printer: URI match: hp:/usb/Photosmart_C4100_series?serial=MY65CB11GY04J7
Sep  9 13:45:08 glenn-desktop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Sep  9 13:45:08 glenn-desktop udev-configure-printer: URI of print queue: hp:/usb/Photosmart_C4100_series?serial=MY65CB11GY04J7, normalized: photosmart c4100 series serial my65cb11gy04j7
Sep  9 13:45:08 glenn-desktop udev-configure-printer: URI of detected printer: usb://HP/Photosmart%20C4100%20series?serial=MY65CB11GY04J7, normalized: photosmart c4100 series serial my65cb11gy04j7
Sep  9 13:45:08 glenn-desktop udev-configure-printer: Queue ipp://localhost:631/printers/Photosmart-C4100-series has matching device URI
Sep  9 13:45:08 glenn-desktop udev-configure-printer: URI of detected printer: hp:/usb/Photosmart_C4100_series?serial=MY65CB11GY04J7, normalized: photosmart c4100 series serial my65cb11gy04j7
Sep  9 13:45:08 glenn-desktop udev-configure-printer: Queue ipp://localhost:631/printers/Photosmart-C4100-series has matching device URI
Sep  9 13:45:16 glenn-desktop kernel: [   59.330020] eth0: no IPv6 routers present
Sep  9 13:45:24 glenn-desktop ntpdate[1402]: adjust time server 66.102.79.92 offset -0.054635 sec
Sep  9 13:45:24 glenn-desktop ntpd[1475]: ntpd 4.2.6p2@1.2194-o Fri Jun 17 06:06:35 UTC 2011 (1)
Sep  9 13:45:24 glenn-desktop ntpd[1476]: proto: precision = 1.396 usec
Sep  9 13:45:24 glenn-desktop ntpd[1476]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen and drop on 1 v6wildcard :: UDP 123
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen normally on 2 lo 127.0.0.1 UDP 123
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen normally on 3 eth0 192.168.1.2 UDP 123
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen normally on 4 eth0 fe80::250:baff:fe1b:cef6 UDP 123
Sep  9 13:45:24 glenn-desktop ntpd[1476]: Listen normally on 5 lo ::1 UDP 123
Sep  9 13:45:26 glenn-desktop init: mythtv-backend main process (1448) terminated with status 254
Sep  9 13:45:26 glenn-desktop init: mythtv-backend main process ended, respawning
Sep  9 13:45:45 glenn-desktop init: mythtv-backend main process (1540) terminated with status 254
Sep  9 13:45:45 glenn-desktop init: mythtv-backend main process ended, respawning
Sep  9 13:46:04 glenn-desktop init: mythtv-backend main process (1606) terminated with status 254
Sep  9 13:46:04 glenn-desktop init: mythtv-backend respawning too fast, stopped
Sep  9 13:54:46 glenn-desktop init: gdm main process (1764) terminated with status 2
Sep  9 13:54:48 glenn-desktop kernel: [  631.175743] mtrr: no MTRR for e0000000,10000000 found
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: Withdrawing address record for 192.168.1.2 on eth0.
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  9 13:55:01 glenn-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  9 13:55:01 glenn-desktop dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Sep  9 13:55:01 glenn-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Sep  9 13:55:01 glenn-desktop init: failsafe-x main process (1766) terminated with status 1
Sep  9 13:55:01 glenn-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: New relevant interface eth0.IPv4 for mDNS.
Sep  9 13:55:01 glenn-desktop avahi-daemon[1062]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Sep  9 13:55:01 glenn-desktop dhclient: bound to 192.168.1.2 -- renewal in 42360 seconds.
Sep  9 13:55:33 glenn-desktop kernel: [  676.530463] show_signal_msg: 12 callbacks suppressed
Sep  9 13:55:33 glenn-desktop kernel: [  676.530469] compiz[2227]: segfault at 0 ip 0000000040035fa8 sp 00007ffff45114c8 error 4 in glVu7zYr (deleted)[40034000+2000]
Sep  9 13:55:34 glenn-desktop kernel: [  677.166095] compiz[2283]: segfault at 0 ip 0000000041b40fa8 sp 00007fff9343efd8 error 4 in gldtYlM5 (deleted)[41b3f000+2000]
Sep  9 13:55:34 glenn-desktop hp-systray: hp-systray[2265]: warning: hp-systray should not be run as root/superuser.
Sep  9 13:55:34 glenn-desktop hp-systray: hp-systray[2265]: error: hp-systray cannot be run as root. Exiting.
Sep  9 13:55:35 glenn-desktop kernel: [  677.880114] compiz[2304]: segfault at 0 ip 0000000041ad7fa8 sp 00007fff43fbaad8 error 4 in glBVDrDK (deleted)[41ad6000+2000]
Sep  9 13:55:36 glenn-desktop anacron[2378]: Anacron 2.3 started on 2011-09-09
Sep  9 13:55:36 glenn-desktop anacron[2378]: Normal exit (0 jobs run)
Sep  9 13:55:36 glenn-desktop kernel: [  679.092149] compiz[2332]: segfault at 0 ip 0000000041175fa8 sp 00007fffb8709078 error 4 in glvI2m94 (deleted)[41174000+2000]
Sep  9 13:55:37 glenn-desktop kernel: [  679.966920] compiz[2397]: segfault at 0 ip 00000000407dcfa8 sp 00007fff32565968 error 4 in glNQiw4X (deleted)[407db000+2000]
Sep  9 13:55:38 glenn-desktop kernel: [  680.773312] compiz[2409]: segfault at 0 ip 0000000040775fa8 sp 00007fffcdddafc8 error 4 in glBCPpkM (deleted)[40774000+2000]
Sep  9 13:55:38 glenn-desktop kernel: [  680.858408] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
Sep  9 13:55:39 glenn-desktop kernel: [  681.800248] compiz[2424]: segfault at 0 ip 0000000041c58fa8 sp 00007fffd1560238 error 4 in gliDNF0Q (deleted)[41c57000+2000]
Sep  9 14:34:31 glenn-desktop kernel: [ 3013.870110] unity-window-de[2280]: segfault at ffffffff ip 00007fc3477492b6 sp 00007fffc7fc48a0 error 4 in libglib-2.0.so.0.2800.6[7fc3476e9000+ed000]
Sep  9 14:34:44 glenn-desktop kernel: [ 3026.701551] unity-window-de[2777]: segfault at ffffffff ip 00007fc8516bd2b6 sp 00007fffdbd231d0 error 4 in libglib-2.0.so.0.2800.6[7fc85165d000+ed000]
Sep  9 14:34:50 glenn-desktop kernel: [ 3032.724153] unity-window-de[2782]: segfault at ffffffff ip 00007f86aaa492b6 sp 00007fff118d7a50 error 4 in libglib-2.0.so.0.2800.6[7f86aa9e9000+ed000]

```

For tail -n300 /var/log/kern.log
```
Sep  9 13:45:04 glenn-desktop kernel: [    0.576887] Freeing initrd memory: 12876k freed
Sep  9 13:45:04 glenn-desktop kernel: [    0.630443] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep  9 13:45:04 glenn-desktop kernel: [    0.990605] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  9 13:45:04 glenn-desktop kernel: [    0.990998] Linux agpgart interface v0.103
Sep  9 13:45:04 glenn-desktop kernel: [    0.992386] brd: module loaded
Sep  9 13:45:04 glenn-desktop kernel: [    0.993029] loop: module loaded
Sep  9 13:45:04 glenn-desktop kernel: [    0.993230] i2c-core: driver [adp5520] using legacy suspend method
Sep  9 13:45:04 glenn-desktop kernel: [    0.993277] i2c-core: driver [adp5520] using legacy resume method
Sep  9 13:45:04 glenn-desktop kernel: [    0.993654] pata_acpi 0000:00:06.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    0.993969] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Sep  9 13:45:04 glenn-desktop kernel: [    0.994035] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Sep  9 13:45:04 glenn-desktop kernel: [    0.994126] pata_acpi 0000:00:07.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    0.994134] pata_acpi 0000:00:07.0: PCI INT A disabled
Sep  9 13:45:04 glenn-desktop kernel: [    0.994417] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [    0.994472] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [    0.994548] pata_acpi 0000:00:08.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    0.994556] pata_acpi 0000:00:08.0: PCI INT A disabled
Sep  9 13:45:04 glenn-desktop kernel: [    0.995165] Fixed MDIO Bus: probed
Sep  9 13:45:04 glenn-desktop kernel: [    0.995251] PPP generic driver version 2.4.2
Sep  9 13:45:04 glenn-desktop kernel: [    0.995354] tun: Universal TUN/TAP device driver, 1.6
Sep  9 13:45:04 glenn-desktop kernel: [    0.995401] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  9 13:45:04 glenn-desktop kernel: [    0.995556] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep  9 13:45:04 glenn-desktop kernel: [    0.995767] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Sep  9 13:45:04 glenn-desktop kernel: [    0.995823] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Sep  9 13:45:04 glenn-desktop kernel: [    0.995895] ehci_hcd 0000:00:02.1: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    0.995898] ehci_hcd 0000:00:02.1: EHCI Host Controller
Sep  9 13:45:04 glenn-desktop kernel: [    0.996028] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Sep  9 13:45:04 glenn-desktop kernel: [    1.030055] ehci_hcd 0000:00:02.1: debug port 1
Sep  9 13:45:04 glenn-desktop kernel: [    1.030105] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
Sep  9 13:45:04 glenn-desktop kernel: [    1.030127] ehci_hcd 0000:00:02.1: irq 21, io mem 0x80100000
Sep  9 13:45:04 glenn-desktop kernel: [    1.050026] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Sep  9 13:45:04 glenn-desktop kernel: [    1.050215] hub 1-0:1.0: USB hub found
Sep  9 13:45:04 glenn-desktop kernel: [    1.050264] hub 1-0:1.0: 10 ports detected
Sep  9 13:45:04 glenn-desktop kernel: [    1.050416] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  9 13:45:04 glenn-desktop kernel: [    1.050650] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Sep  9 13:45:04 glenn-desktop kernel: [    1.050712] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Sep  9 13:45:04 glenn-desktop kernel: [    1.050781] ohci_hcd 0000:00:02.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    1.050784] ohci_hcd 0000:00:02.0: OHCI Host Controller
Sep  9 13:45:04 glenn-desktop kernel: [    1.050879] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Sep  9 13:45:04 glenn-desktop kernel: [    1.090049] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf5002000
Sep  9 13:45:04 glenn-desktop kernel: [    1.152174] hub 2-0:1.0: USB hub found
Sep  9 13:45:04 glenn-desktop kernel: [    1.152223] hub 2-0:1.0: 10 ports detected
Sep  9 13:45:04 glenn-desktop kernel: [    1.152365] uhci_hcd: USB Universal Host Controller Interface driver
Sep  9 13:45:04 glenn-desktop kernel: [    1.152550] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Sep  9 13:45:04 glenn-desktop kernel: [    1.152598] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep  9 13:45:04 glenn-desktop kernel: [    1.153462] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  9 13:45:04 glenn-desktop kernel: [    1.154320] mousedev: PS/2 mouse device common for all mice
Sep  9 13:45:04 glenn-desktop kernel: [    1.154503] rtc_cmos 00:04: RTC can wake from S4
Sep  9 13:45:04 glenn-desktop kernel: [    1.174997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Sep  9 13:45:04 glenn-desktop kernel: [    1.190083] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Sep  9 13:45:04 glenn-desktop kernel: [    1.190154] rtc0: alarms up to one year, y3k, 242 bytes nvram
Sep  9 13:45:04 glenn-desktop kernel: [    1.190317] device-mapper: uevent: version 1.0.3
Sep  9 13:45:04 glenn-desktop kernel: [    1.190459] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Sep  9 13:45:04 glenn-desktop kernel: [    1.190626] device-mapper: multipath: version 1.2.0 loaded
Sep  9 13:45:04 glenn-desktop kernel: [    1.190675] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep  9 13:45:04 glenn-desktop kernel: [    1.190878] cpuidle: using governor ladder
Sep  9 13:45:04 glenn-desktop kernel: [    1.190926] cpuidle: using governor menu
Sep  9 13:45:04 glenn-desktop kernel: [    1.191304] TCP cubic registered
Sep  9 13:45:04 glenn-desktop kernel: [    1.191486] NET: Registered protocol family 10
Sep  9 13:45:04 glenn-desktop kernel: [    1.192069] NET: Registered protocol family 17
Sep  9 13:45:04 glenn-desktop kernel: [    1.192136] Registering the dns_resolver key type
Sep  9 13:45:04 glenn-desktop kernel: [    1.192212] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 cpu cores) (version 2.20.00)
Sep  9 13:45:04 glenn-desktop kernel: [    1.192329] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
Sep  9 13:45:04 glenn-desktop kernel: [    1.192376] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Sep  9 13:45:04 glenn-desktop kernel: [    1.192596] PM: Hibernation image not present or could not be loaded.
Sep  9 13:45:04 glenn-desktop kernel: [    1.192617] registered taskstats version 1
Sep  9 13:45:04 glenn-desktop kernel: [    1.192912]   Magic number: 11:288:746
Sep  9 13:45:04 glenn-desktop kernel: [    1.192992] pci_express 0000:00:0d.0:pcie08: hash matches
Sep  9 13:45:04 glenn-desktop kernel: [    1.193132] rtc_cmos 00:04: setting system clock to 2011-09-09 18:44:18 UTC (1315593858)
Sep  9 13:45:04 glenn-desktop kernel: [    1.193189] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  9 13:45:04 glenn-desktop kernel: [    1.193236] EDD information not available.
Sep  9 13:45:04 glenn-desktop kernel: [    1.195215] Freeing unused kernel memory: 956k freed
Sep  9 13:45:04 glenn-desktop kernel: [    1.195833] Write protecting the kernel read-only data: 10240k
Sep  9 13:45:04 glenn-desktop kernel: [    1.196711] Freeing unused kernel memory: 184k freed
Sep  9 13:45:04 glenn-desktop kernel: [    1.202247] Freeing unused kernel memory: 1440k freed
Sep  9 13:45:04 glenn-desktop kernel: [    1.228074] <30>udev[98]: starting version 167
Sep  9 13:45:04 glenn-desktop kernel: [    1.296881] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Sep  9 13:45:04 glenn-desktop kernel: [    1.297181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Sep  9 13:45:04 glenn-desktop kernel: [    1.297235] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Sep  9 13:45:04 glenn-desktop kernel: [    1.297296] forcedeth 0000:00:0a.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    1.362652] via-rhine.c:v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
Sep  9 13:45:04 glenn-desktop kernel: [    1.370100] usb 1-7: new high speed USB device using ehci_hcd and address 2
Sep  9 13:45:04 glenn-desktop kernel: [    1.371742] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Sep  9 13:45:04 glenn-desktop kernel: [    1.371819] via-rhine 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Sep  9 13:45:04 glenn-desktop kernel: [    1.376291] eth0: VIA Rhine II at 0xf4005000, 00:50:ba:1b:ce:f6, IRQ 16.
Sep  9 13:45:04 glenn-desktop kernel: [    1.377045] eth0: MII PHY found at address 8, status 0x782d advertising 01e1 Link 4de1.
Sep  9 13:45:04 glenn-desktop kernel: [    1.380923] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Sep  9 13:45:04 glenn-desktop kernel: [    1.380996] firewire_ohci 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Sep  9 13:45:04 glenn-desktop kernel: [    1.440091] firewire_ohci: Added fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Sep  9 13:45:04 glenn-desktop kernel: [    1.821025] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x3f1 @ 7, addr 00:14:85:10:f2:18
Sep  9 13:45:04 glenn-desktop kernel: [    1.821088] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
Sep  9 13:45:04 glenn-desktop kernel: [    1.821602] pata_amd 0000:00:06.0: version 0.4.1
Sep  9 13:45:04 glenn-desktop kernel: [    1.821656] pata_amd 0000:00:06.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    1.822233] scsi0 : pata_amd
Sep  9 13:45:04 glenn-desktop kernel: [    1.822609] scsi1 : pata_amd
Sep  9 13:45:04 glenn-desktop kernel: [    1.823134] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Sep  9 13:45:04 glenn-desktop kernel: [    1.823183] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Sep  9 13:45:04 glenn-desktop kernel: [    1.823443] sata_nv 0000:00:07.0: version 3.5
Sep  9 13:45:04 glenn-desktop kernel: [    1.823458] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Sep  9 13:45:04 glenn-desktop kernel: [    1.823574] sata_nv 0000:00:07.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    1.823876] scsi2 : sata_nv
Sep  9 13:45:04 glenn-desktop kernel: [    1.824018] scsi3 : sata_nv
Sep  9 13:45:04 glenn-desktop kernel: [    1.824193] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xcc00 irq 23
Sep  9 13:45:04 glenn-desktop kernel: [    1.824242] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xcc08 irq 23
Sep  9 13:45:04 glenn-desktop kernel: [    1.824384] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [    1.824490] sata_nv 0000:00:08.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    1.824762] scsi4 : sata_nv
Sep  9 13:45:04 glenn-desktop kernel: [    1.824903] scsi5 : sata_nv
Sep  9 13:45:04 glenn-desktop kernel: [    1.825064] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe000 irq 22
Sep  9 13:45:04 glenn-desktop kernel: [    1.825114] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe008 irq 22
Sep  9 13:45:04 glenn-desktop kernel: [    1.860063] usb 1-9: new high speed USB device using ehci_hcd and address 4
Sep  9 13:45:04 glenn-desktop kernel: [    1.940153] firewire_core: created device fw0: GUID 00148556000f37dc, S800
Sep  9 13:45:04 glenn-desktop kernel: [    2.000381] ata1.00: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
Sep  9 13:45:04 glenn-desktop kernel: [    2.000432] ata1.00: 156301488 sectors, multi 16: LBA 
Sep  9 13:45:04 glenn-desktop kernel: [    2.000487] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
Sep  9 13:45:04 glenn-desktop kernel: [    2.019249] usbcore: registered new interface driver uas
Sep  9 13:45:04 glenn-desktop kernel: [    2.020355] ata1.00: configured for UDMA/100
Sep  9 13:45:04 glenn-desktop kernel: [    2.020606] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.020881] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  9 13:45:04 glenn-desktop kernel: [    2.020923] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Sep  9 13:45:04 glenn-desktop kernel: [    2.020973] sd 0:0:0:0: [sda] Write Protect is off
Sep  9 13:45:04 glenn-desktop kernel: [    2.020976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  9 13:45:04 glenn-desktop kernel: [    2.020998] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  9 13:45:04 glenn-desktop kernel: [    2.049862]  sda: sda1 sda2 < sda5 >
Sep  9 13:45:04 glenn-desktop kernel: [    2.050432] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  9 13:45:04 glenn-desktop kernel: [    2.130029] usb 1-10: new high speed USB device using ehci_hcd and address 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.150083] ata5: SATA link down (SStatus 0 SControl 300)
Sep  9 13:45:04 glenn-desktop kernel: [    2.220272] ata2.00: ATAPI: HITACHI GD-2000, 0056, max MWDMA2
Sep  9 13:45:04 glenn-desktop kernel: [    2.220324] ata2.01: ATAPI: HL-DT-ST GCE-8400B, 1.02, max MWDMA2
Sep  9 13:45:04 glenn-desktop kernel: [    2.220378] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:120:0x1a)
Sep  9 13:45:04 glenn-desktop kernel: [    2.220383] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:120:0x1a)
Sep  9 13:45:04 glenn-desktop kernel: [    2.260204] ata2.00: configured for MWDMA2
Sep  9 13:45:04 glenn-desktop kernel: [    2.293285] Initializing USB Mass Storage driver...
Sep  9 13:45:04 glenn-desktop kernel: [    2.293553] scsi6 : usb-storage 1-9:1.3
Sep  9 13:45:04 glenn-desktop kernel: [    2.293841] scsi7 : usb-storage 1-10:1.0
Sep  9 13:45:04 glenn-desktop kernel: [    2.294013] usbcore: registered new interface driver usb-storage
Sep  9 13:45:04 glenn-desktop kernel: [    2.294062] USB Mass Storage support registered.
Sep  9 13:45:04 glenn-desktop kernel: [    2.300235] ata2.01: configured for MWDMA2
Sep  9 13:45:04 glenn-desktop kernel: [    2.310039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  9 13:45:04 glenn-desktop kernel: [    2.330301] ata3.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Sep  9 13:45:04 glenn-desktop kernel: [    2.330350] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep  9 13:45:04 glenn-desktop kernel: [    2.330836] scsi 1:0:0:0: CD-ROM            HITACHI  GD-2000          0056 PQ: 0 ANSI: 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.361111] sr0: scsi3-mmc drive: 8x/20x cd/rw xa/form2 cdda tray
Sep  9 13:45:04 glenn-desktop kernel: [    2.361160] cdrom: Uniform CD-ROM driver Revision: 3.20
Sep  9 13:45:04 glenn-desktop kernel: [    2.361369] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep  9 13:45:04 glenn-desktop kernel: [    2.361475] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.361868] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  1.02 PQ: 0 ANSI: 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.370321] ata3.00: configured for UDMA/133
Sep  9 13:45:04 glenn-desktop kernel: [    2.372919] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Sep  9 13:45:04 glenn-desktop kernel: [    2.373078] sr 1:0:1:0: Attached scsi CD-ROM sr1
Sep  9 13:45:04 glenn-desktop kernel: [    2.373148] sr 1:0:1:0: Attached scsi generic sg2 type 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.373389] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Sep  9 13:45:04 glenn-desktop kernel: [    2.373641] sd 2:0:0:0: Attached scsi generic sg3 type 0
Sep  9 13:45:04 glenn-desktop kernel: [    2.373791] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  9 13:45:04 glenn-desktop kernel: [    2.373917] sd 2:0:0:0: [sdb] Write Protect is off
Sep  9 13:45:04 glenn-desktop kernel: [    2.373965] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  9 13:45:04 glenn-desktop kernel: [    2.373988] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  9 13:45:04 glenn-desktop kernel: [    2.415132]  sdb: sdb1 sdb2 < sdb5 >
Sep  9 13:45:04 glenn-desktop kernel: [    2.415532] sd 2:0:0:0: [sdb] Attached SCSI disk
Sep  9 13:45:04 glenn-desktop kernel: [    2.620075] usb 2-8: new low speed USB device using ohci_hcd and address 2
Sep  9 13:45:04 glenn-desktop kernel: [    2.700034] ata4: SATA link down (SStatus 0 SControl 300)
Sep  9 13:45:04 glenn-desktop kernel: [    2.910136] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-8/2-8:1.0/input/input3
Sep  9 13:45:04 glenn-desktop kernel: [    2.910329] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-8/input0
Sep  9 13:45:04 glenn-desktop kernel: [    2.920657] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-8/2-8:1.1/input/input4
Sep  9 13:45:04 glenn-desktop kernel: [    2.920839] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-8/input1
Sep  9 13:45:04 glenn-desktop kernel: [    2.920918] usbcore: registered new interface driver usbhid
Sep  9 13:45:04 glenn-desktop kernel: [    2.920966] usbhid: USB HID core driver
Sep  9 13:45:04 glenn-desktop kernel: [    3.030024] ata6: SATA link down (SStatus 0 SControl 300)
Sep  9 13:45:04 glenn-desktop kernel: [    3.292480] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
Sep  9 13:45:04 glenn-desktop kernel: [    3.293937] sd 6:0:0:0: Attached scsi generic sg4 type 0
Sep  9 13:45:04 glenn-desktop kernel: [    3.294152] scsi 7:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
Sep  9 13:45:04 glenn-desktop kernel: [    3.296848] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Sep  9 13:45:04 glenn-desktop kernel: [    3.300303] sd 7:0:0:0: Attached scsi generic sg5 type 0
Sep  9 13:45:04 glenn-desktop kernel: [    3.302855] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Sep  9 13:45:04 glenn-desktop kernel: [    3.384639] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Sep  9 13:45:04 glenn-desktop kernel: [    5.591998] Adding 2096124k swap on /dev/sdb5.  Priority:-1 extents:1 across:2096124k 
Sep  9 13:45:04 glenn-desktop kernel: [    6.211969] <30>udev[417]: starting version 167
Sep  9 13:45:04 glenn-desktop kernel: [    8.646152] nvidia: module license 'NVIDIA' taints kernel.
Sep  9 13:45:04 glenn-desktop kernel: [    8.646158] Disabling lock debugging due to kernel taint
Sep  9 13:45:04 glenn-desktop kernel: [    9.255175] MCE: In-kernel MCE decoding enabled.
Sep  9 13:45:04 glenn-desktop kernel: [    9.260425] parport_pc 00:09: reported by Plug and Play ACPI
Sep  9 13:45:04 glenn-desktop kernel: [    9.260470] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep  9 13:45:04 glenn-desktop kernel: [    9.296145] ppdev: user-space parallel port driver
Sep  9 13:45:04 glenn-desktop kernel: [    9.484089] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Sep  9 13:45:04 glenn-desktop kernel: [    9.484104] nvidia 0000:05:00.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [    9.484111] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep  9 13:45:04 glenn-desktop kernel: [    9.485183] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Sep  9 13:45:04 glenn-desktop kernel: [    9.515267] EDAC MC: Ver: 2.1.0 Aug 29 2011
Sep  9 13:45:04 glenn-desktop kernel: [    9.588023] Linux video capture interface: v2.00
Sep  9 13:45:04 glenn-desktop kernel: [    9.607590] EDAC amd64_edac: v3.3.0
Sep  9 13:45:04 glenn-desktop kernel: [    9.607763] EDAC amd64: DRAM ECC disabled.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607777] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607778]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Sep  9 13:45:04 glenn-desktop kernel: [    9.607780]  (Note that use of the override may cause unknown side effects.)
Sep  9 13:45:04 glenn-desktop kernel: [    9.673108] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)
Sep  9 13:45:04 glenn-desktop kernel: [    9.689210] input: UVC Camera (046d:08c9) as /devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/input/input5
Sep  9 13:45:04 glenn-desktop kernel: [    9.689345] usbcore: registered new interface driver uvcvideo
Sep  9 13:45:04 glenn-desktop kernel: [    9.689348] USB Video Class driver (v1.0.0)
Sep  9 13:45:04 glenn-desktop kernel: [    9.700091] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Sep  9 13:45:04 glenn-desktop kernel: [    9.700146] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
Sep  9 13:45:04 glenn-desktop kernel: [    9.726103] lp0: using parport0 (interrupt-driven).
Sep  9 13:45:04 glenn-desktop kernel: [   10.104974] type=1400 audit(1315593867.397:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.105357] type=1400 audit(1315593867.397:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.105603] type=1400 audit(1315593867.397:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106282] type=1400 audit(1315593867.397:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106662] type=1400 audit(1315593867.397:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.106910] type=1400 audit(1315593867.397:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.107618] type=1400 audit(1315593867.397:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.108002] type=1400 audit(1315593867.397:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.108260] type=1400 audit(1315593867.397:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   10.112415] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [   10.112423] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
Sep  9 13:45:04 glenn-desktop kernel: [   10.112455] Intel ICH 0000:00:04.0: setting latency timer to 64
Sep  9 13:45:04 glenn-desktop kernel: [   10.321882] usbcore: registered new interface driver snd-usb-audio
Sep  9 13:45:04 glenn-desktop kernel: [   10.429879] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
Sep  9 13:45:04 glenn-desktop kernel: [   10.430342] usbcore: registered new interface driver usblp
Sep  9 13:45:04 glenn-desktop kernel: [   10.450037] intel8x0_measure_ac97_clock: measured 50048 usecs (2464 samples)
Sep  9 13:45:04 glenn-desktop kernel: [   10.450042] intel8x0: clocking to 46798
Sep  9 13:45:04 glenn-desktop kernel: [   10.495992] type=1400 audit(1315593867.787:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=899 comm="apparmor_parser"
Sep  9 13:45:04 glenn-desktop kernel: [   46.721343] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Sep  9 13:45:05 glenn-desktop kernel: [   47.712574] audit_printk_skb: 6 callbacks suppressed
Sep  9 13:45:05 glenn-desktop kernel: [   47.712579] type=1400 audit(1315593905.016:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.712985] type=1400 audit(1315593905.016:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.713236] type=1400 audit(1315593905.016:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1024 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.846923] type=1400 audit(1315593905.146:17): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1023 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945050] type=1400 audit(1315593905.246:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1039 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945077] type=1400 audit(1315593905.246:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1045 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945524] type=1400 audit(1315593905.246:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1039 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   47.945562] type=1400 audit(1315593905.246:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1045 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   48.297968] type=1400 audit(1315593905.596:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1025 comm="apparmor_parser"
Sep  9 13:45:05 glenn-desktop kernel: [   48.303152] type=1400 audit(1315593905.606:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1025 comm="apparmor_parser"
Sep  9 13:45:06 glenn-desktop kernel: [   49.180958] eth0: link up, 100Mbps, full-duplex, lpa 0x4DE1
Sep  9 13:45:06 glenn-desktop kernel: [   49.271954] forcedeth 0000:00:0a.0: eth1: no link during initialization
Sep  9 13:45:06 glenn-desktop kernel: [   49.272714] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  9 13:45:07 glenn-desktop kernel: [   50.124278] usb 1-9: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Sep  9 13:45:16 glenn-desktop kernel: [   59.330020] eth0: no IPv6 routers present
Sep  9 13:54:48 glenn-desktop kernel: [  631.175743] mtrr: no MTRR for e0000000,10000000 found
Sep  9 13:55:33 glenn-desktop kernel: [  676.530463] show_signal_msg: 12 callbacks suppressed
Sep  9 13:55:33 glenn-desktop kernel: [  676.530469] compiz[2227]: segfault at 0 ip 0000000040035fa8 sp 00007ffff45114c8 error 4 in glVu7zYr (deleted)[40034000+2000]
Sep  9 13:55:34 glenn-desktop kernel: [  677.166095] compiz[2283]: segfault at 0 ip 0000000041b40fa8 sp 00007fff9343efd8 error 4 in gldtYlM5 (deleted)[41b3f000+2000]
Sep  9 13:55:35 glenn-desktop kernel: [  677.880114] compiz[2304]: segfault at 0 ip 0000000041ad7fa8 sp 00007fff43fbaad8 error 4 in glBVDrDK (deleted)[41ad6000+2000]
Sep  9 13:55:36 glenn-desktop kernel: [  679.092149] compiz[2332]: segfault at 0 ip 0000000041175fa8 sp 00007fffb8709078 error 4 in glvI2m94 (deleted)[41174000+2000]
Sep  9 13:55:37 glenn-desktop kernel: [  679.966920] compiz[2397]: segfault at 0 ip 00000000407dcfa8 sp 00007fff32565968 error 4 in glNQiw4X (deleted)[407db000+2000]
Sep  9 13:55:38 glenn-desktop kernel: [  680.773312] compiz[2409]: segfault at 0 ip 0000000040775fa8 sp 00007fffcdddafc8 error 4 in glBCPpkM (deleted)[40774000+2000]
Sep  9 13:55:38 glenn-desktop kernel: [  680.858408] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
Sep  9 13:55:39 glenn-desktop kernel: [  681.800248] compiz[2424]: segfault at 0 ip 0000000041c58fa8 sp 00007fffd1560238 error 4 in gliDNF0Q (deleted)[41c57000+2000]
Sep  9 14:34:31 glenn-desktop kernel: [ 3013.870110] unity-window-de[2280]: segfault at ffffffff ip 00007fc3477492b6 sp 00007fffc7fc48a0 error 4 in libglib-2.0.so.0.2800.6[7fc3476e9000+ed000]
Sep  9 14:34:44 glenn-desktop kernel: [ 3026.701551] unity-window-de[2777]: segfault at ffffffff ip 00007fc8516bd2b6 sp 00007fffdbd231d0 error 4 in libglib-2.0.so.0.2800.6[7fc85165d000+ed000]
Sep  9 14:34:50 glenn-desktop kernel: [ 3032.724153] unity-window-de[2782]: segfault at ffffffff ip 00007f86aaa492b6 sp 00007fff118d7a50 error 4 in libglib-2.0.so.0.2800.6[7f86aa9e9000+ed000]

```

---

### Post by wildmanne39 on 2011-09-10
Hi, post the results of this command please:
```
lspci | grep VGA

```
```
sudo lshw
```
Thank you

---

### Post by GlennW on 2011-11-05
> **wildmanne39 said:**
> Hi, post the results of this command please:
```
lspci | grep VGA

```
```
sudo lshw
```
Thank you

Sorry that I haven't responded sooner but things have been crazy.

This is pretty awkward since I am having to save outputs to a file, shut down, and mount a different drive to be able to access the file.

lspci | grep VGA output:

05:00.0 VGA compatible controller: nVidia Corporation G71 (GeForce 7951 ST) (rev a1)

sudo lshw output:

```
glenn-desktop
    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: GA-K8N Pro-SLI
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3
          date: 02/10/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          product: Athlon
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3GHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2008MiB
        *-bank:0
             description: DIMM 166 MHz (6.0 ns) [empty]
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:1
             description: DIMM 166 MHz (6.0 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:2
             description: DIMM 166 MHz (6.0 ns) [empty]
             physical id: 2
             slot: A2
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:3
             description: DIMM 166 MHz (6.0 ns) [empty]
             physical id: 3
             slot: A3
             width: 64 bits
             clock: 166MHz (6.0ns)
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:11 ioport:e400(size=32) ioport:1c00(size=64) ioport:1c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:f5002000-f5002fff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:80100000-801000ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:b400(size=256) ioport:b800(size=256) memory:f5005000-f5005fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi4
          logical name: scsi5
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-disk
             description: ATA Disk
             product: WDC WD800JB-00JJ
             vendor: Western Digital
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 05.0
             serial: WD-WCAM9D901853
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00014921
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/991dfd16-5dc7-4b5f-b305-b8e64b05d5b5
                version: 1.0
                serial: 991dfd16-5dc7-4b5f-b305-b8e64b05d5b5
                size: 71GiB
                capacity: 71GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-06-25 18:42:13 filesystem=ext4 lastmountpoint=/ modified=2011-11-05 12:38:25 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-11-05 12:38:25 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                size: 3152MiB
                capacity: 3152MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 3152MiB
                   capabilities: nofs
        *-cdrom:0
             description: DVD reader
             product: GD-2000
             vendor: HITACHI
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0056
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/scd1
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:cc00(size=16) memory:f5000000-f5000fff
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC38
             serial: 6VP4QQRD
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0007f5d9
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 10556174-9e0a-4b43-a7c0-be295aaa412b
                size: 929GiB
                capacity: 929GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-05-04 14:41:42 filesystem=ext4 lastmountpoint=/ modified=2011-11-05 12:34:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-11-05 12:38:22 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2047MiB
                capacity: 2047MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2047MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:e000(size=16) memory:f5001000-f5001fff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
          resources: ioport:9000(size=4096) memory:f3000000-f4ffffff memory:80000000-800fffff
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 8
             bus info: pci@0000:01:08.0
             logical name: eth0
             version: 43
             serial: 00:50:ba:1b:ce:f6
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.11 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:16 ioport:9000(size=256) memory:f4005000-f40050ff memory:80000000-8000ffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB82AA2 IEEE-1394b Link Layer Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
             resources: irq:18 memory:f4004000-f40047ff memory:f4000000-f4003fff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth1
          version: a3
          serial: 00:14:85:10:f2:18
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:23 memory:f5003000-f5003fff ioport:e800(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:6000(size=4096)
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:8000(size=4096)
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:7000(size=4096)
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:43 ioport:a000(size=4096) memory:f0000000-f2ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G71 [GeForce 7950 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:f0000000-f0ffffff memory:e0000000-efffffff memory:f1000000-f1ffffff ioport:a000(size=128) memory:f2000000-f201ffff
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 10
          bus info: usb@1:9
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C4180
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdc
```

---

### Post by GlennW on 2011-11-05
> **wildmanne39 said:**
> Hi, did you install upgrades like for video card or the kernel just before this happened? 

Did you try what I posted in post 7?

It sounds like there may be a different issue now also.

A long time ago I did an upgrade and I was never able to get the upgraded kernel to work but that was before I learned a few things.

If you can get back into recovery run these commands and it should tell us what is going on.
```
dmesg |tail -n300
```
```
tail -n300 /var/log/syslog
```
```
tail -n300 /var/log/kern.log
```
Thank you

I tried to follow the instructions in post #7 but I couldn't get anywhere. 

I made a new startup USB stick from the latest Ubuntu 11.10 64-bit iso and attempted to run it. My laptop boots fine from it but the desktop box will not. The screen is purple with nothing on it, no cursor, not anything. As I mentioned in an earlier post, I have two drives on the desktop box. The 1TB drive (the one that will not boot off the USB and that is giving me this trouble) and an 80 GB drive running 10.04. The 80 GB drive mounts without incident.  I can mount the 1TB and access its files but that's it.

Any further suggestions?

Thanks for your time on this.

---

### Post by GlennW on 2011-11-07
Anyone?

---

### Post by BillyBoa on 2011-11-07
Looks like a hardware problem to me.

---

### Post by GlennW on 2011-11-08
> **BillyBoa said:**
> Looks like a hardware problem to me.

What would make you think that? Details are crucial in this case.

Thanks.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-08
I don't know how to solve your problem, but as a quick fix you could run a live session (puppy works really well as a live session... it is very small and loads completely in memory) [Puppy Linux News]("http://puppylinuxnews.org/")
It is pretty simple to use.

---

### Post by GlennW on 2011-11-09
> **TREESofRIGHTEOUSNESS said:**
> I don't know how to solve your problem, but as a quick fix you could run a live session (puppy works really well as a live session... it is very small and loads completely in memory) [Puppy Linux News]("http://puppylinuxnews.org/")
It is pretty simple to use.

I would run a live session if possible. I cannot boot from a live usb. Please read my earlier posts for details. I have checked the live usb and it works in every other box that I've tried without issue. 

My very limited understanding of Linux/Ubuntu would suggest that this is a grub/boot issue. I know there is a grub repair tool that is run via a live session but not being able to boot from a live usb renders this option nonviable. 

I also surmise that this is not a hardware issue due to the fact that I am running the box currently having mounted an older drive. (See older post for these details.)

Thanks for your time on this.

---

