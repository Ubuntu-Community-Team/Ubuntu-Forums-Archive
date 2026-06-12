---
title: "Need help in resolving slow boot time"
date: 2009-04-23
forum: General Help
---

### Post by olivierp on 2009-04-23
After having upgraded with no issues to 9.04, I'm trying to fix a "nuisance" I've had _at least_ since 8.10, if not before. I have NEVER had to reinstall from scratch since Edgy, always doing an upgrade (once or twice with an RC in the middle)

Searching for this has only lead to "I've reinstalled, problem gone", or to fixes for other modules. Note that apart from the long boot time (close to 3 minutes until GDM starts), everything works fine.
Each boot gets stuck for at least a minute on "Loading hardware modules". This apparently relates to udev setting up the hardware. Here's the relevant part from dmesg:
```
[    9.418512] sd 5:0:0:3: Attached scsi generic sg7 type 0
[   12.280761] udev: starting version 141
[   22.461178] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   22.656259] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   22.656348] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   22.774918] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   22.774974] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[   22.775196] Intel ICH 0000:00:04.0: setting latency timer to 64
[   23.096029] intel8x0_measure_ac97_clock: measured 54722 usecs
[   23.096083] intel8x0: clocking to 46904
[   32.484985] Linux agpgart interface v0.103
[   32.673800] nvidia: module license 'NVIDIA' taints kernel.
[   32.934133] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   32.934195] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   32.934262] nvidia 0000:01:00.0: setting latency timer to 64
[   32.935264] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   42.873545] parport_pc 00:09: reported by Plug and Play ACPI
[   42.873644] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   52.799825] usbcore: registered new interface driver hiddev
[   52.805445] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
[   52.807053] generic-usb 0003:046D:C318.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:02.0-4/input0
[   52.816244] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input5
[   52.819603] generic-usb 0003:046D:C318.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:02.0-4/input1
[   52.824422] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input6
[   52.826004] generic-usb 0003:046D:C526.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-5/input0
[   52.836239] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.1/input/input7
[   52.850354] generic-usb 0003:046D:C526.0004: input,hiddev97,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-5/input1
[   52.850443] usbcore: registered new interface driver usbhid
[   52.850512] usbhid: v2.6:USB HID core driver
[   52.944026] ppdev: user-space parallel port driver
[   53.034478] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7111
[   53.034573] usbcore: registered new interface driver usblp
[   93.129672] lp0: using parport0 (interrupt-driven).
```Any hints as to what is causing the 10 to 40 sec waits and where I could try to fix them ?

---

