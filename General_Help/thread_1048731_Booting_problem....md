---
title: "Booting problem..."
date: 2009-01-23
forum: General Help
---

### Post by Crafty Kisses on 2009-01-23
So I have a Windows Vista / Ubuntu 8.10 dual-boot, but every time I boot back into Ubuntu from Windows, I'll get a message about ACPI, it goes by too fast. Then I hear my motherboard beeping, the beeping doesn't stop until I reboot. Not sure what's causing this, it's fixed with only one reboot, and that fixes it every time until I reboot back into Windows and try to boot back into Ubuntu. So I ran the following command:
```
dmesg | grep ACPI
```
The results of that command:
```
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F9FD0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT BFFA0000, 0048 (r1 GATEWA SYSTEM   20080214 MSFT       97)
[    0.000000] ACPI: FACP BFFA0200, 0084 (r1 021408 FACP1340 20080214 MSFT       97)
[    0.000000] ACPI: DSDT BFFA0620, 5D77 (r1  A7399 A7399105      105 INTL 20051117)
[    0.000000] ACPI: FACS BFFAE000, 0040
[    0.000000] ACPI: APIC BFFA0390, 0080 (r1 021408 APIC1340 20080214 MSFT       97)
[    0.000000] ACPI: MCFG BFFA0410, 003C (r1 021408 OEMMCFG  20080214 MSFT       97)
[    0.000000] ACPI: SLIC BFFA0450, 0176 (r1 GATEWA SYSTEM   20080214 MSFT       97)
[    0.000000] ACPI: WDRT BFFA05D0, 0047 (r1 021408 NV-WDRT  20080214 MSFT       97)
[    0.000000] ACPI: OEMB BFFAE040, 0071 (r1 021408 OEMB1340 20080214 MSFT       97)
[    0.000000] ACPI: HPET BFFA63A0, 0038 (r1 021408 OEMHPET0 20080214 MSFT       97)
[    0.000000] ACPI: NVHD BFFAE0C0, 0554 (r1 021408  NVHDCP  20080214 MSFT       97)
[    0.000000] ACPI: SSDT BFFAEF40, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.006479] ACPI: Core revision 20080609
[    0.007835] ACPI: Checking initramfs for custom DSDT
[    0.464322] ACPI: bus type pci registered
[    0.464845] ACPI: EC: Look up EC in DSDT
[    0.476368] ACPI: Interpreter enabled
[    0.476370] ACPI: (supports S0 S1 S3 S4 S5)
[    0.476385] ACPI: Using IOAPIC for interrupt routing
[    0.482465] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.496221] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.500659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.500939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.501107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.501221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.501335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.512274] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.512532] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.512783] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.513035] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.513285] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.513539] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *10
[    0.513789] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.514039] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.514294] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.514554] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.514808] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.515061] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *7
[    0.515311] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.515566] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.516213] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.516471] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.516769] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.516823] pnp: PnP ACPI init
[    0.516823] ACPI: bus type pnp registered
[    0.521214] pnp: PnP ACPI: found 12 devices
[    0.521216] ACPI: ACPI bus type pnp unregistered
[    0.521234] PCI: Using ACPI for IRQ routing
[    0.543557] ACPI: RTC can wake from S4
[    1.569786] ACPI: SSDT BFFAE620, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.570135] processor ACPI0007:00: registered as cooling_device0
[    1.570138] ACPI: Processor [P001] (supports 8 throttling states)
[    1.570467] ACPI: SSDT BFFAEAB0, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.570792] processor ACPI0007:01: registered as cooling_device1
[    1.572458] ACPI: Expecting a [Reference] package element, found type C
[    1.598850] ACPI: Thermal Zone [THRM] (41 C)
[    1.910185] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    2.172898] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    2.556335] ata1: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    2.574457] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    4.028656] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    9.524532] ACPI: Power Button (FF) [PWRF]
[    9.560530] ACPI: Power Button (CM) [PWRB]
[    9.771225] ACPI: WMI: Mapper loaded
[   10.663547] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[   11.137541] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   11.137922] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23

```
Not really sure what's causing this, I rarely boot into my Windows partition, but when I do this tends to happen. Not sure why, any ideas?

---

### Post by elchtzeasar on 2009-01-24
I have almost the exact same problem, except that I do not have to boot into Vista to get this (I do have a vista installation though). I have included an extraction from kern.log when it happens.

The message I get together with the beep is:
```
ACPI: Expecting a [Reference] package element, found type C
```

Here is an extraction of the entries around this:
```
Jan 23 22:49:00 peter-laptop kernel: [    1.373959] EDD information not available.
Jan 23 22:49:00 peter-laptop kernel: [    1.373990] Freeing unused kernel memory: 536k freed
Jan 23 22:49:00 peter-laptop kernel: [    1.374154] Write protecting the kernel read-only data: 4348k
Jan 23 22:49:00 peter-laptop kernel: [    1.410607] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 23 22:49:00 peter-laptop kernel: [    1.528575] fuse init (API version 7.9)
Jan 23 22:49:00 peter-laptop kernel: [    1.592458] ACPI: SSDT BFF96BC0, 0248 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.593015] ACPI: SSDT BFF96EA0, 0765 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.593829] Monitor-Mwait will be used to enter C-1 state
Jan 23 22:49:00 peter-laptop kernel: [    1.593831] Monitor-Mwait will be used to enter C-3 state
Jan 23 22:49:00 peter-laptop kernel: [    1.593954] ACPI: CPU0 (power states: C1[C1] C2[C3])
Jan 23 22:49:00 peter-laptop kernel: [    1.593998] processor ACPI0007:00: registered as cooling_device0
Jan 23 22:49:00 peter-laptop kernel: [    1.594001] ACPI: Processor [P001] (supports 8 throttling states)
Jan 23 22:49:00 peter-laptop kernel: [    1.594329] ACPI: SSDT BFF96AF0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.594736] ACPI: SSDT BFF96E10, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.600004] Marking TSC unstable due to TSC halts in idle
Jan 23 22:49:00 peter-laptop kernel: [    1.612274] ACPI: CPU1 (power states: C1[C1] C2[C3])
Jan 23 22:49:00 peter-laptop kernel: [    1.612344] processor ACPI0007:01: registered as cooling_device1
Jan 23 22:49:00 peter-laptop kernel: [    1.612347] ACPI: Processor [P002] (supports 8 throttling states)
Jan 23 22:49:00 peter-laptop kernel: [    1.616173] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 23 22:49:00 peter-laptop kernel: [    1.666318] ACPI: Expecting a [Reference] package element, found type C
Jan 23 22:49:00 peter-laptop kernel: [    1.666726] thermal LNXTHERM:01: registered as thermal_zone0
Jan 23 22:49:00 peter-laptop kernel: [    1.669560] ACPI: Thermal Zone [THRM] (40 C)
Jan 23 22:49:00 peter-laptop kernel: [    2.014429] usbcore: registered new interface driver usbfs
Jan 23 22:49:00 peter-laptop kernel: [    2.014449] usbcore: registered new interface driver hub
Jan 23 22:49:00 peter-laptop kernel: [    2.015832] usbcore: registered new device driver usb
Jan 23 22:49:00 peter-laptop kernel: [    2.022298] USB Universal Host Controller Interface driver v3.0
Jan 23 22:49:00 peter-laptop kernel: [    2.022344] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 22:49:00 peter-laptop kernel: [    2.022354] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.022359] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.022398] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 23 22:49:00 peter-laptop kernel: [    2.022436] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
Jan 23 22:49:00 peter-laptop kernel: [    2.022575] usb usb1: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.022611] hub 1-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.022616] hub 1-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.073225] No dock devices found.
Jan 23 22:49:00 peter-laptop kernel: [    2.125267] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 23 22:49:00 peter-laptop kernel: [    2.125278] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.125281] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.125303] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jan 23 22:49:00 peter-laptop kernel: [    2.125339] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Jan 23 22:49:00 peter-laptop kernel: [    2.125415] usb usb2: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.125436] hub 2-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.125441] hub 2-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.147821] SCSI subsystem initialized
Jan 23 22:49:00 peter-laptop kernel: [    2.174640] libata version 3.00 loaded.
Jan 23 22:49:00 peter-laptop kernel: [    2.229336] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 23 22:49:00 peter-laptop kernel: [    2.229346] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.229349] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.229371] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Jan 23 22:49:00 peter-laptop kernel: [    2.229408] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
Jan 23 22:49:00 peter-laptop kernel: [    2.229487] usb usb3: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.229507] hub 3-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.229513] hub 3-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.437398] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 23 22:49:00 peter-laptop kernel: [    1.373959] EDD information not available.
Jan 23 22:49:00 peter-laptop kernel: [    1.373990] Freeing unused kernel memory: 536k freed
Jan 23 22:49:00 peter-laptop kernel: [    1.374154] Write protecting the kernel read-only data: 4348k
Jan 23 22:49:00 peter-laptop kernel: [    1.410607] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 23 22:49:00 peter-laptop kernel: [    1.528575] fuse init (API version 7.9)
Jan 23 22:49:00 peter-laptop kernel: [    1.592458] ACPI: SSDT BFF96BC0, 0248 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.593015] ACPI: SSDT BFF96EA0, 0765 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.593829] Monitor-Mwait will be used to enter C-1 state
Jan 23 22:49:00 peter-laptop kernel: [    1.593831] Monitor-Mwait will be used to enter C-3 state
Jan 23 22:49:00 peter-laptop kernel: [    1.593954] ACPI: CPU0 (power states: C1[C1] C2[C3])
Jan 23 22:49:00 peter-laptop kernel: [    1.593998] processor ACPI0007:00: registered as cooling_device0
Jan 23 22:49:00 peter-laptop kernel: [    1.594001] ACPI: Processor [P001] (supports 8 throttling states)
Jan 23 22:49:00 peter-laptop kernel: [    1.594329] ACPI: SSDT BFF96AF0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.594736] ACPI: SSDT BFF96E10, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Jan 23 22:49:00 peter-laptop kernel: [    1.600004] Marking TSC unstable due to TSC halts in idle
Jan 23 22:49:00 peter-laptop kernel: [    1.612274] ACPI: CPU1 (power states: C1[C1] C2[C3])
Jan 23 22:49:00 peter-laptop kernel: [    1.612344] processor ACPI0007:01: registered as cooling_device1
Jan 23 22:49:00 peter-laptop kernel: [    1.612347] ACPI: Processor [P002] (supports 8 throttling states)
Jan 23 22:49:00 peter-laptop kernel: [    1.616173] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 23 22:49:00 peter-laptop kernel: [    1.666318] ACPI: Expecting a [Reference] package element, found type C
Jan 23 22:49:00 peter-laptop kernel: [    1.666726] thermal LNXTHERM:01: registered as thermal_zone0
Jan 23 22:49:00 peter-laptop kernel: [    1.669560] ACPI: Thermal Zone [THRM] (40 C)
Jan 23 22:49:00 peter-laptop kernel: [    2.014429] usbcore: registered new interface driver usbfs
Jan 23 22:49:00 peter-laptop kernel: [    2.014449] usbcore: registered new interface driver hub
Jan 23 22:49:00 peter-laptop kernel: [    2.015832] usbcore: registered new device driver usb
Jan 23 22:49:00 peter-laptop kernel: [    2.022298] USB Universal Host Controller Interface driver v3.0
Jan 23 22:49:00 peter-laptop kernel: [    2.022344] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 22:49:00 peter-laptop kernel: [    2.022354] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.022359] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.022398] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 23 22:49:00 peter-laptop kernel: [    2.022436] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
Jan 23 22:49:00 peter-laptop kernel: [    2.022575] usb usb1: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.022611] hub 1-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.022616] hub 1-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.073225] No dock devices found.
Jan 23 22:49:00 peter-laptop kernel: [    2.125267] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 23 22:49:00 peter-laptop kernel: [    2.125278] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.125281] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.125303] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jan 23 22:49:00 peter-laptop kernel: [    2.125339] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Jan 23 22:49:00 peter-laptop kernel: [    2.125415] usb usb2: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.125436] hub 2-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.125441] hub 2-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.147821] SCSI subsystem initialized
Jan 23 22:49:00 peter-laptop kernel: [    2.174640] libata version 3.00 loaded.
Jan 23 22:49:00 peter-laptop kernel: [    2.229336] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 23 22:49:00 peter-laptop kernel: [    2.229346] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Jan 23 22:49:00 peter-laptop kernel: [    2.229349] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jan 23 22:49:00 peter-laptop kernel: [    2.229371] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Jan 23 22:49:00 peter-laptop kernel: [    2.229408] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
Jan 23 22:49:00 peter-laptop kernel: [    2.229487] usb usb3: configuration #1 chosen from 1 choice
Jan 23 22:49:00 peter-laptop kernel: [    2.229507] hub 3-0:1.0: USB hub found
Jan 23 22:49:00 peter-laptop kernel: [    2.229513] hub 3-0:1.0: 2 ports detected
Jan 23 22:49:00 peter-laptop kernel: [    2.437398] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18

``` 

Let me know if you need anything more and Ill provide it!

---

### Post by Crafty Kisses on 2009-01-24
Thanks a million for that bit of information, that's the exact error I'm getting. From my research and my own doings, I think it may have something to do with the BIOS, or a USB device. It seems that if I add the following line in GRUB, the problem dies down a little bit.
```
quiet
```
I also figured out it happens more if I have my USB headset plugged in, but If I unplug it and boot into Linux, it sometimes happens, but If the USB headset is plugged in, it happens every time. Upon further research someone suggested on another forum to update their BIOS as they had the same problem as us, so any more information you get on this please update me.

---

### Post by Crafty Kisses on 2009-01-26
So I'm not sure if this information will help you, but I've noticed if I do a cold reboot the problem is solved, I don't get the ACPI error anymore, well at least I haven't yet. So that  has toned the problem down a lot. I've also noticed if I add the following line to the Linux kernel, it seems to tone it down a bit also:
```
noacpi
```
The problem still occurs, but the error message stays up longer, and also with this in the kernel I also noticed I can actually sometimes have a USB device plugged in without that error coming up, where before like 95% of the time, the error would come up with a USB device plugged in, then I tried a different line to add in my kernel which is:
```
acpi=off
```
The problem is almost gone, but I still get the error from time to time. I hope this helps my friend, this error is really weird and sometimes random it doesn't make any sense, but my methods should work a little bit, also remember the USB devices, unplug any you may have before you boot Ubuntu.

---

### Post by elchtzeasar on 2009-01-28
I found this thread: [http://ubuntuforums.org/showthread.php?p=6598597](http://ubuntuforums.org/showthread.php?p=6598597) where someone managed to solve it by disabling the splash screen. That seems to have worked for me, I have not seen the error in a couple of days since doing this. 

Hope this helps...

---

### Post by Crafty Kisses on 2009-01-30
Thanks for the reply my good friend, I will try this later and see if it works.

---

### Post by billstei on 2009-04-24
I am also getting this error on boot-up with Jaunty 9.04 

ACPI: Expecting a [Reference] package element, found type C

---

### Post by Crafty Kisses on 2009-05-05
> **billstei said:**
> I am also getting this error on boot-up with Jaunty 9.04 

ACPI: Expecting a [Reference] package element, found type C

Hey there, thanks for responding to this thread. When you get that error message does Ubuntu still boot?

---

### Post by billstei on 2009-05-15
> **Codename said:**
> Hey there, thanks for responding to this thread. When you get that error message does Ubuntu still boot?

Yes it boots, after a very short pause to show the error message.

Might have something to do with the thermal module, as this message:

  thermal LNXTHERM:01: registered as thermal_zone0

occurs right afterward in the dmesg list.

---

### Post by Trebacz on 2009-09-19
I've also had the same issue of the message showing when booting for years:

The sequence of messages in my system log are

```
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484438] ACPI Warning (nspredef-0858): \_TZ_.THRM._TZD: Return Package type mismatch at index 0 - found Processor, expected Reference [20080926]
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484445] ACPI: Expecting a [Reference] package element, found type C
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484569] thermal LNXTHERM:01: registered as thermal_zone0
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484724] ACPI: Thermal Zone [THRM] (80 C)

```

Doesn't seem to have any negative effects, just annoying. Perhaps it does have something to do with the hardware or BIOS incorrectly reporting a temperature sensor that does or doesn't exist.

My motherboard is an MSI MS-7252 with version V5.6 (09/06/2007) of their BIOS. There are two update to my BIOS from MSI, but I don't want to attempt that unless I know it will solve the problem.

- Disabled PCI Prefetch.
- Update CPU ID.
- Update NB module.
- Fixed AMD Cool&Quiet cannot work properly under Vista 64 bit.

---

### Post by Crafty Kisses on 2009-09-20
> **Trebacz said:**
> I've also had the same issue of the message showing when booting for years:

The sequence of messages in my system log are

```
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484438] ACPI Warning (nspredef-0858): \_TZ_.THRM._TZD: Return Package type mismatch at index 0 - found Processor, expected Reference [20080926]
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484445] ACPI: Expecting a [Reference] package element, found type C
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484569] thermal LNXTHERM:01: registered as thermal_zone0
Sep 19 08:44:14 AMD-ubuntu kernel: [    1.484724] ACPI: Thermal Zone [THRM] (80 C)

```

Doesn't seem to have any negative effects, just annoying. Perhaps it does have something to do with the hardware or BIOS incorrectly reporting a temperature sensor that does or doesn't exist.

My motherboard is an MSI MS-7252 with version V5.6 (09/06/2007) of their BIOS. There are two update to my BIOS from MSI, but I don't want to attempt that unless I know it will solve the problem.

- Disabled PCI Prefetch.
- Update CPU ID.
- Update NB module.
- Fixed AMD Cool&Quiet cannot work properly under Vista 64 bit.
Yeah. I'm not sure if a BIOS update would solve the issue or not. I can just tell you it gets quite annoying and requires a reboot because the board will not stop making the beeping noise.

---

