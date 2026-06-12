---
title: "System does not power off (will now halt)"
date: 2006-07-02
forum: Desktop Environments
---

### Post by chambis on 2006-07-02
Dear masters...
I know that this issue has been posted several times but unfortunally i haven't been able to sove my problem yet. 
I use dapper whit xgl/compiz installed and everything works just perfect.
My basic problem is that after shut doen computer stops at "will now halt" without powering off

I have been searching for days and i found suggestions such as:

1) Edit the /boot/grub/menu.lst and add apm=force or acpi=force or lapic

2) install older version of my xorg-driver-fglrx (basically the problem exists even if i use ati instaed of the fglrx drivers)

3) install the bug fix from the official site.

Unfortunately NONE of this worked and i have a huge problem now

In addition i would like to mention that the problem existed just as i have upgraded from breezy to dapper (not in breezy) and even before i installed xgl/xompiz

* Actually i think that it is a power management problem and i am not sure if it has to do with the fglrx drivers as well
So i decited to post these:
When i type

dmesg | grep -i acpi
I get these results:
> [17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb090
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000409 MSFT 0x00000097) @ 0x3ffc0000
[17179569.184000] ACPI: FADT (v001 A M I  OEMFACP  0x06000409 MSFT 0x00000097) @ 0x3ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000409 MSFT 0x00000097) @ 0x3ffc0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000409 MSFT 0x00000097) @ 0x3ffce040
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000409 MSFT 0x00000097) @ 0x3ffc5ff0
[17179569.184000] ACPI: DSDT (v001  A0045 A0045001 0x00000001 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash acpi=force
[17179572.936000] ACPI: Looking for DSDT ... not found!
[17179573.192000] ACPI: bus type pci registered
[17179573.192000] ACPI: Subsystem revision 20051216
[17179573.200000] ACPI: Interpreter enabled
[17179573.200000] ACPI: Using IOAPIC for interrupt routing
[17179573.200000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.204000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179573.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179573.208000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[17179573.216000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.216000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.216000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.216000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.220000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.220000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.220000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.220000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.220000] pnp: PnP ACPI init
[17179573.224000] pnp: PnP ACPI: found 19 devices
[17179573.224000] PnPBIOS: Disabled by ACPI PNP
[17179573.224000] PCI: Using ACPI for IRQ routing
[17179573.244000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.244000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.244000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.244000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.244000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.244000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.668000] ACPI wakeup devices:
[17179573.668000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.984000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.628000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 217
[17179577.284000] ACPI: bus type scsi registered
[17179577.288000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179582.636000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179582.668000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179582.856000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179582.964000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179583.072000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179594.036000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.480000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179594.596000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179595.796000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 66
[17179599.524000] ACPI: Power Button (FF) [PWRF]
[17179599.524000] ACPI: Power Button (CM) [PWRB]
[17179599.616000] ibm_acpi: ec object not found
[17179599.652000] pcc_acpi: loading...
[17179606.740000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 169


dmesg | grep -i apm
> [17179608.092000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.092000] apm: disabled - APM is not SMP safe.


dmesg | grep -i error
> [17179637.292000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179637.316000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179637.316000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715ab00 for 5242880 bytes
[17179637.436000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179637.456000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179637.456000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715a640 for 5242880 bytes
[17179637.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179637.492000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179637.492000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715a680 for 5242880 bytes
[17179638.876000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179638.896000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179638.896000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715abc0 for 5242880 bytes
[17179638.904000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179638.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179638.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715ab40 for 5242880 bytes
[17179639.424000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xac3f9000 for 5242880 bytes
[17179639.444000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179639.444000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715ab80 for 5242880 bytes
[17179651.184000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08b0b000 for 163840 bytes
[17179651.188000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179651.188000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715a940 for 163840 bytes
[17179652.796000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa99b7000 for 5242880 bytes
[17179652.820000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179652.820000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf74cd140 for 5242880 bytes
[17179658.860000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bea000 for 262144 bytes
[17179658.864000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179658.864000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xebda6980 for 262144 bytes
[17179660.712000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa9d83000 for 1261568 bytes
[17179660.716000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179660.716000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xebda6880 for 1261568 bytes
[17179669.160000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8bd1000 for 5079040 bytes
[17179669.184000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179669.184000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb9c0 for 5079040 bytes
[17179674.720000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08c53000 for 262144 bytes
[17179674.724000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179674.724000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xebda67c0 for 262144 bytes
[17179676.128000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa9d83000 for 1261568 bytes
[17179676.132000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179676.132000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf79b8e80 for 1261568 bytes
[17179677.728000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8bd1000 for 5079040 bytes
[17179677.752000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179677.756000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf79b8580 for 5079040 bytes
[17179684.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 49152 bytes
[17179684.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179684.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xdfb5e580 for 49152 bytes
[17179685.436000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08b97000 for 8192 bytes
[17179685.436000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.436000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb1c0 for 8192 bytes
[17179685.440000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8ba9000 for 5242880 bytes
[17179685.460000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.460000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb200 for 5242880 bytes
[17179685.460000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 196608 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb400 for 196608 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08b97000 for 8192 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb3c0 for 8192 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 32768 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb340 for 32768 bytes
[17179685.464000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 344064 bytes
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb380 for 344064 bytes
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 57344 bytes
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb300 for 57344 bytes
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 229376 bytes
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.468000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb2c0 for 229376 bytes
[17179685.472000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 540672 bytes
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb280 for 540672 bytes
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 98304 bytes
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb240 for 98304 bytes
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 393216 bytes
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.476000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818afc0 for 393216 bytes
[17179685.480000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 688128 bytes
[17179685.484000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.484000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818af80 for 688128 bytes
[17179685.484000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 139264 bytes
[17179685.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818af40 for 139264 bytes
[17179685.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 557056 bytes
[17179685.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818af00 for 557056 bytes
[17179685.496000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 835584 bytes
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818aec0 for 835584 bytes
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 180224 bytes
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818ae80 for 180224 bytes
[17179685.500000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 720896 bytes
[17179685.504000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.504000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818ae40 for 720896 bytes
[17179685.512000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8fb9000 for 983040 bytes
[17179685.520000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.520000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818ae00 for 983040 bytes
[17179685.520000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08bcd000 for 221184 bytes
[17179685.524000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.524000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818adc0 for 221184 bytes
[17179685.524000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8fd1000 for 884736 bytes
[17179685.528000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179685.528000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818ad80 for 884736 bytes
[17179688.912000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7daf000 for 5079040 bytes
[17179688.940000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179688.940000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xdfbf3d40 for 5079040 bytes
[17179689.932000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa810c000 for 532480 bytes
[17179689.932000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179689.932000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715a480 for 532480 bytes
[17179719.672000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08dd0000 for 16384 bytes
[17179719.672000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179719.672000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xebda6780 for 16384 bytes
[17179725.520000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa81c6000 for 286720 bytes
[17179725.524000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179725.524000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf71bb180 for 286720 bytes
[17179846.928000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa80c9000 for 196608 bytes
[17179846.928000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179846.928000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818aa40 for 196608 bytes
[17179851.044000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7f95000 for 327680 bytes
[17179851.048000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179851.048000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe227a6c0 for 327680 bytes
[17179869.740000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08d97000 for 16384 bytes
[17179869.740000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179869.740000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe227a640 for 16384 bytes
[17179896.096000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa80c9000 for 196608 bytes
[17179896.100000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179896.100000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818a940 for 196608 bytes
[17179900.392000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7f95000 for 327680 bytes
[17179900.396000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179900.396000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818a9c0 for 327680 bytes
[17179923.664000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa80c9000 for 196608 bytes
[17179923.664000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179923.664000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818ac80 for 196608 bytes
[17179927.728000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08c8c000 for 24576 bytes
[17179927.728000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179927.728000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xebda62c0 for 24576 bytes
[17179932.732000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7674000 for 5079040 bytes
[17179932.752000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179932.756000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xdf945780 for 5079040 bytes
[17179935.840000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7f95000 for 327680 bytes
[17179935.840000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179935.840000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe227aa80 for 327680 bytes
[17179965.196000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa80c9000 for 196608 bytes
[17179965.200000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179965.200000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe818a140 for 196608 bytes
[17179965.836000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7f7b000 for 221184 bytes
[17179965.840000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179965.840000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf715aa00 for 221184 bytes


Help needed please
Thank you in advance

---

