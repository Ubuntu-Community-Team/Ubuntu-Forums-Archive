---
title: "Emulator problems"
date: 2010-12-20
forum: Gaming &amp; Leisure
---

### Post by HikariKurayami on 2010-12-20
I ran pSX from a terminal, got this immediately after I run it


(pSX:14182): GdkGLExt-WARNING **: Cannot open &#575;\x82
L.so


after I start a game, it will crash before I even get to the game.

as for snes9x and my other ones, they run fine, but my controller used to give out randomly for snes9x and pSX only, then it just started giving out and acting weird with pretty much everything, and I think it may be due to having "Joystick" on my computer to try a fix, but that didn't do anything for me, so help, please!

also, my specs are (on Ubuntu 9.10 Karmic):

desktop-hp-linux-ubuntu   
    description: Desktop Computer
    product: NY535AA-ABA MS214
    vendor: HP-Pavilion
    version: None
    serial: 4CS94300TL
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=desktop cpus=2 uuid=00821EC0-142F-1510-908D-DD72CE445D66
  *-core
       description: Motherboard
       product: Capirona
       vendor: Hewlett-Packard
       physical id: 0
       serial: QTCZN110F94008474
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V5.11 (08/28/2009)
          size: 116KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) X2 Dual Core Processor 3250e
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.2
          slot: Socket S1G2
          size: 1500MHz
          capacity: 1500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T2864EH3-CF7
             vendor: CE00000000000000
             physical id: 0
             serial: 75C7E6F3
             slot: S1
             size: 1GiB
             width: 16 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T2864EH3-CF7
             vendor: CE00000000000000
             physical id: 1
             serial: 75C7E6FC
             slot: S2
             size: 1GiB
             width: 16 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.11.2
          size: 1500MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: Hewlett-Packard Company
             vendor: Hewlett-Packard Company
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:f8200000-f83fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:30 memory:e0000000-efffffff(prefetchable) ioport:9000(size=256) memory:f8300000-f830ffff memory:f8200000-f82fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:a000(size=8192) memory:f8000000-f81fffff
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:17:c4:be:f9:6d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:f8000000-f800ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:c000(size=4096) memory:80000000-800fffff ioport:f8800000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: 00:26:9e:49:08:42
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=67.174.72.149 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:29 ioport:c000(size=256) memory:f8810000-f8810fff(prefetchable) memory:f8800000-f880ffff(prefetchable) memory:f8820000-f883ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 memory:f8400000-f84fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f8400000-f84000ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:0a:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f8400400-f84004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:0a:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:f8400800-f84008ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:0a:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:f8400c00-f8400cff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8430(size=8) ioport:8424(size=4) ioport:8428(size=8) ioport:8420(size=4) ioport:8400(size=16) memory:f8708000-f87083ff
           *-disk
                description: ATA Disk
                product: WDC WD3200AAJS-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAV27401695
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1549f232
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4c0fa10d-97ab-4b15-951e-a12f42f0426f
                   size: 293GiB
                   capacity: 293GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-15 02:33:35 filesystem=ext4 lastmountpoint=/K&#65533;F&#65533;c&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x^&#65533;f&#65533;&#65533;(&#65533;&#65533;&#65533;(&#65533;&#65533;c&#65533;&#65533;^&#65533;^&#65533;i&#65533;c&#65533;&#65533;&&#65533;&#65533;&#65533; modified=2010-12-20 02:06:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-12-20 11:40:41 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5153MiB
                   capacity: 5153MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5153MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT20L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f8704000-f8704fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f8705000-f8705fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f8708400-f87084ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f8706000-f8706fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f8707000-f8707fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f8708800-f87088ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f8700000-f8703fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

used sudo lshw to get that.

---

### Post by HikariKurayami on 2010-12-20
I know it's long, but I'd really like a response, it'd make me feel better, and plus I might be able to fix this, I hope, and if anyone wanted to know, it's 32-bit.

---

### Post by Philsoki on 2010-12-20
> used sudo lshw to get that.
Thanks for that, I was looking through your system specs and was about to ask you how you got that when I saw it at the bottom of the screen. :)

> I know it's long, but I'd really like a response, it'd make me feel  better, and plus I might be able to fix this, I hope, and if anyone  wanted to know, it's 32-bit.
Did you download the emulator from the website or from the Software Centre?

---

### Post by HikariKurayami on 2010-12-20
> **Philsoki said:**
> Thanks for that, I was looking through your system specs and was about to ask you how you got that when I saw it at the bottom of the screen. :)


Did you download the emulator from the website or from the Software Centre?

snes9x and pSX I did, but as for Mupen64+ and GFCEU, I downloaded those from the repositories with Synaptic
and actually, I'm not sure if it's completely emulator-related, but I'm hoping that it is

---

### Post by Philsoki on 2010-12-20
> **HikariKurayami said:**
> snes9x and pSX I did, but as for Mupen64+ and GFCEU, I downloaded those from the repositories with Synaptic
So you downloaded pSX from the website? I'll download it and see if it works for me or if I get the same error. I've never used this emulator so I probably won't be of much help, but hey it's worth a try...

---

### Post by HikariKurayami on 2010-12-20
> **Philsoki said:**
> So you downloaded pSX from the website? I'll download it and see if it works for me or if I get the same error. I've never used this emulator so I probably won't be of much help, but hey it's worth a try...

thanks, but as I edited in, I'm not sure if it's completely the emulator as a whole, it may be many conflicting things on my computer, or maybe something I don't have for my controller and/or emulators that I need, maybe it's just my hardware, I don't really know, exactly.

Edit: rather, what I'm trying to say is it may just be my problem and it may not show at all for you.

---

### Post by Philsoki on 2010-12-20
> **HikariKurayami said:**
> thanks, but as I edited in, I'm not sure if it's completely the emulator as a whole, it may be many conflicting things on my computer, or maybe something I don't have for my controller and/or emulators that I need, maybe it's just my hardware, I don't really know, exactly.
Well, the emulator was a really small file so I have that now.

I forgot to ask, did you download the bios file (SCPH1001.bin) ?

---

### Post by HikariKurayami on 2010-12-20
yes, I did, I've got plenty

Edit: I've got 1 of that particular one, but I have like 12 or so different ones (no multiples)

---

### Post by Philsoki on 2010-12-20
Cool, did you put the SCPH1001.bin in the bios directory?

---

### Post by HikariKurayami on 2010-12-20
I set up everything exactly how it should be, there's nothing wrong with the setup, it's just executing the whole thing, it won't play any games, it freezes right after the playstation thing comes up the red and yellow P.

Edit: snes9x also freezes up rather frequently now, although I'm sure none of this SHOULD be happening, it is, and I have absolutely no idea why. Mupen64+ has problems and so does GFCEU on a smaller level (as in controller level)

by the way, my controller is a Logitech Rumblepad 2 (corded)

---

### Post by Philsoki on 2010-12-20
Copy and paste this into the software centre: OpenGL Extension to GTK+ (shared libraries)
There should only be one file that comes up, install it. Then try the emulator again.

> **HikariKurayami said:**
> I set up everything exactly how it should be, there's nothing wrong with the setup, it's just executing the whole thing, it won't play any games, it freezes right after the playstation thing comes up the red and yellow P.

Edit: snes9x also freezes up rather frequently now, although I'm sure none of this SHOULD be happening, it is, and I have absolutely no idea why. Mupen64+ has problems and so does GFCEU on a smaller level (as in controller level)

by the way, my controller is a Logitech Rumblepad 2 (corded)

Are you using the open or closed (source) drivers? I haven't ever used one of there cards, but from what I've heard the drivers are a bit fiddly. I think the open driver is better for 2D (e.g. Snes) while the closed source driver is better for 3D. (e.g. N64).

Do you have compositing effects enabled? Does the desktop cube work? Turn compositing effects off if you have them enabled.

---

### Post by HikariKurayami on 2010-12-20
> **Philsoki said:**
> Copy and paste this into the software centre: OpenGL Extension to GTK+ (shared libraries)
There should only be one file that comes up, install it. Then try the emulator again.

I think I have it, I checked in Synaptic

> **Philsoki said:**
> Are you using the open or closed (source) drivers? I haven't ever used one of there cards, but from what I've heard the drivers are a bit fiddly. I think the open driver is better for 2D (e.g. Snes) while the closed source driver is better for 3D. (e.g. N64).

Do you have compositing effects enabled? Does the desktop cube work? Turn compositing effects off if you have them enabled.

I got the drivers from System -> Admin -> Hardware Drivers
I don't know about compositing effects.
Edit: I hope I got the quote things right...

---

### Post by Philsoki on 2010-12-20
> I don't know about compositing effects.
Right Click on you desktop > Change Desktop Background > Choose "Visual Effects" tab and set it to "none".

> I got the drivers from System -> Admin -> Hardware Drivers
Is it the open or closed source driver? (I don't use an ATI card so I don't know much about it...)

---

### Post by HikariKurayami on 2010-12-20
> **Philsoki said:**
> Is it the open or closed source driver? (I don't use an ATI card so I don't know much about it...)

More than likely, the closed source driver.

Edit: I tried reducing the visual effects, but I hated it, I don't like it, so I'm sticking with my current ones, and besides, this only just started happening fairly recently, so it's weird

---

### Post by Philsoki on 2010-12-20
Well, I'm stumped. I'd like to help out more but I have to go and get ready for work now... :(

I'll go out on a limb here and suggest PCSX and ePSXe, I've never actually tried them. Just thought I'd throw out the alternatives I know of.

I hope you (or someone on here) can get the emulator working. Good luck.

---

### Post by HikariKurayami on 2010-12-20
Thanks anyway, but like I said, it may be hardware and I should be having someone over on Wednesday (conveniently) who should be able to help with any problems (Hardware and Software, whatever I need, he'll probably be able to help)

---

### Post by Philsoki on 2010-12-21
> **HikariKurayami said:**
> Thanks anyway, but like I said, it may be hardware and I should be having someone over on Wednesday (conveniently) who should be able to help with any problems (Hardware and Software, whatever I need, he'll probably be able to help)
Cool. Hopefully they can get it working. If they/you do, could you post up how you did it?

---

### Post by HikariKurayami on 2010-12-21
> **Philsoki said:**
> Cool. Hopefully they can get it working. If they/you do, could you post up how you did it?

for sure, no problem.

---

### Post by HikariKurayami on 2010-12-24
As of right now, I believe it's my controller or USB ports (I'm betting more on the former, however) My emu problems, however, are most likely a result of not having the right settings or just plain ignorance about how these should work on Ubuntu, but I will fix them somehow and take care of my problems. (If it /is/ the USB ports, however, I will be back.)

---

### Post by HikariKurayami on 2011-01-04
Okay, so, I am stumped still. pSX seems to give me different messages when I run it, but I've noticed one thing that's certainly weird.


Invalid rate plugin version 10002

(pSX:2566): GdkGLExt-WARNING **: Cannot open Ho\xe2	L.so
sound: underrun
sound: underrun
Invalid rate plugin version 10002

That was from the first time I ran it, and this:


Invalid rate plugin version 10002

(pSX:2643): GdkGLExt-WARNING **: Cannot open \xb8\xed4
L.so
sound: underrun
Invalid rate plugin version 10002
Invalid rate plugin version 10002
Invalid rate plugin version 10002

was the second.

Call me crazy, but I see a pattern here, now I think that the sound underrun problems could probably be killed by killing pulseaudio, but what I don't get is, what are these files that it can't open?

---

