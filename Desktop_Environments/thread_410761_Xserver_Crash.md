---
title: "Xserver Crash"
date: 2007-04-16
forum: Desktop Environments
---

### Post by Vuddha on 2007-04-16
Hi,

I posted a question a couple of days ago in this forum regarding a suspected Xserver crash ("Logout error?").

The advice I was given was the enter certain commands in the terminal next time it crashes and post the information here.

I was surfing the internet (actually on the Ubuntu website, cbc.ca, and gamesindustry.biz) and there was no flash or video, and no other apps running.  

Here is the output from the terminal:

vu@vu-laptop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

vu@vu-laptop:~$ dmesg | tail -n 100
[17179594.408000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179594.408000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
[17179594.408000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179594.408000] Yenta O2: enabling read prefetch/write burst
[17179594.536000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179594.536000] Socket status: 30000006
[17179594.536000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179594.536000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[17179594.536000] cs: IO port probe 0xd000-0xefff: clean.
[17179594.536000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[17179594.536000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179594.536000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179594.536000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
[17179594.664000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179594.664000] Socket status: 30000410
[17179594.664000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179594.664000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[17179594.664000] cs: IO port probe 0xd000-0xefff: clean.
[17179594.664000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[17179594.664000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179594.668000] tg3.c:v3.59.1 (August 25, 2006)
[17179594.668000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179594.708000] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:7b:6c:44
[17179594.708000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179594.708000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[17179594.708000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179594.708000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset c (was df570000, writing 0)
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset b (was 164714e4, writing 81261028)
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 4008)
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset 2 (was 2000000, writing 2000002)
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2b00000, writing 2b00104)
[17179595.132000] PM: Writing back config space on device 0000:02:00.0 at offset 0 (was 164714e4, writing 16a614e4)
[17179595.468000] pccard: PCMCIA card inserted into slot 1
[17179595.468000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xfa1fffff 0xfae00000-0xfb3fffff
[17179595.472000] pcmcia: registering new device pcmcia1.0
[17179595.524000] cs: IO port probe 0x100-0x3af: clean.
[17179595.528000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179595.528000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.528000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.528000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.572000] cs: IO port probe 0x100-0x3af: clean.
[17179595.572000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179595.572000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.572000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.572000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.684000] lp0: using parport0 (interrupt-driven).
[17179595.752000] fuse init (API version 7.6)
[17179595.776000] Adding 979956k swap on /dev/disk/by-uuid/72dff085-44bb-49f7-85e3-374a4c4cc222.  Priority:-1 extents:1 across:979956k
[17179595.884000] EXT3 FS on hda1, internal journal
[17179596.052000] kjournald starting.  Commit interval 5 seconds
[17179596.060000] EXT3 FS on hda2, internal journal
[17179596.060000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.456000] NET: Registered protocol family 17
[17179600.892000] ACPI: AC Adapter [AC] (on-line)
[17179601.220000] ACPI: Battery Slot [BAT0] (battery present)
[17179601.220000] ACPI: Battery Slot [BAT1] (battery absent)
[17179601.236000] ACPI: Lid Switch [LID]
[17179601.236000] ACPI: Power Button (CM) [PBTN]
[17179601.236000] ACPI: Sleep Button (CM) [SBTN]
[17179601.276000] ACPI: ACPI Dock Station Driver 
[17179601.428000] ibm_acpi: ec object not found
[17179601.460000] pcc_acpi: loading...
[17179601.584000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179604.028000] [drm] Initialized drm 1.0.1 20051102
[17179604.096000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179604.100000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179604.652000] apm: BIOS not found.
[17179605.568000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17179605.568000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17179605.568000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17179605.568000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179605.568000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179605.568000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179605.824000] [drm] Setting GART location based on new memory map
[17179605.824000] [drm] Loading R200 Microcode
[17179605.824000] [drm] writeback test succeeded in 2 usecs
[17179609.252000] Bluetooth: Core ver 2.8
[17179609.252000] NET: Registered protocol family 31
[17179609.252000] Bluetooth: HCI device and connection manager initialized
[17179609.252000] Bluetooth: HCI socket layer initialized
[17179609.300000] Bluetooth: L2CAP ver 2.8
[17179609.300000] Bluetooth: L2CAP socket layer initialized
[17179609.368000] Bluetooth: RFCOMM socket layer initialized
[17179609.368000] Bluetooth: RFCOMM TTY layer initialized
[17179609.368000] Bluetooth: RFCOMM ver 1.7
[17179619.084000] NET: Registered protocol family 10
[17179619.084000] lo: Disabled Privacy Extensions
[17179619.084000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179619.084000] IPv6 over IPv4 tunneling driver
[17179629.100000] eth1: no IPv6 routers present
[17180118.040000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17180118.040000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17180118.040000] mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x2000000
[17180118.040000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17180118.040000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17180118.040000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17180118.260000] [drm] Setting GART location based on new memory map
[17180118.260000] [drm] Loading R200 Microcode
[17180118.260000] [drm] writeback test succeeded in 2 usecs


If this is an xserver crash, why is it occurring when i use Firefox?  It seems to be happening daily.

Thanks,
--Vu

---

