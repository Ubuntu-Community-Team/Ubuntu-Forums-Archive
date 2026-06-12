---
title: "Parallel Port Printing Problem"
date: 2009-02-28
forum: General Help
---

### Post by Yumi on 2009-02-28
After starting the computer most of the time the printer is not working. Sometimes a message appears informing that the Printer is not attached.

I checked other threads, installed extra software, made sure the printer is enabled in Admin - Printing.

> lsmod | grep par
parport_pc             39204  3 
parport                42604  3 ppdev,lp,parport_pc

lp seems to be recognised

Here is a problem with sysctl:
> $ dmesg | grep par
[    0.440027] Booting paravirtualized kernel on bare hardware
[    0.470134] pci 0000:00:10.0: transparent bridge
[    5.695733] PM: Resume from partition 8:6
[   15.769041] parport_pc 00:06: reported by Plug and Play ACPI
[   15.769179] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   15.784054] parport0: Printer, Hewlett-Packard HP LaserJet 1100
[   19.953627] lp0: using parport0 (interrupt-driven).
[   35.666059] ppdev: user-space parallel port driver
[   36.378654] ppdev0: registered pardevice
[   40.414125] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists
[   40.414280]  [<f8a37aa4>] parport_device_proc_register+0xb4/0xe0 [parport]
[   40.414298]  [<f8a35951>] parport_register_device+0x151/0x240 [parport]
[   40.414320]  [<f8a35604>] ? parport_find_number+0x74/0x90 [parport]
[   40.414413] ppdev0: registered pardevice
[   41.076158] ppdev0: unregistered pardevice
[ 1334.587117] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists
[ 1334.587269]  [<f8a37aa4>] parport_device_proc_register+0xb4/0xe0 [parport]
[ 1334.587288]  [<f8a35951>] parport_register_device+0x151/0x240 [parport]
[ 1334.587311]  [<f8a35604>] ? parport_find_number+0x74/0x90 [parport]
[ 1334.587413] ppdev0: registered pardevice

Any help/advice?

Michael

---

