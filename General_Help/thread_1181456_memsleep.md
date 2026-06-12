---
title: "memsleep??"
date: 2009-06-07
forum: General Help
---

### Post by z4r4thustr4 on 2009-06-07
Had a weird episode earlier today...Dell Latitude D600 with Jaunty starts to act strange.  i was in emacs and could not write the buffer I was working on.  switching to terminal and issuing top hangs, as does ls.  The filesystem is suddenly read-only.

the first restart boot in normal mode FAILS.  restart seems to show that system cannot shut down properly.

system suddenly works again, but everything I've done has been purely diagnostic.  had a kernel panic at some point.

at first i think the hard drive has bit it, but smartmontools (smartctl) shows nothing of consequence.  built in memory tests are fine as well.  

e2fsck in single user mode shows nothing of consequence.  my system logs at the time seem to indicate that memory just decided to shut down.  


Jun  7 16:40:34 kryptonite kernel: [ 9824.382210] PM: Syncing filesystems ... done.
Jun  7 16:40:34 kryptonite kernel: [ 9824.395916] PM: Preparing system for mem sleep
Jun  7 16:40:34 kryptonite kernel: [ 9824.395923] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jun  7 16:40:34 kryptonite kernel: [ 9824.397688] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jun  7 16:40:34 kryptonite kernel: [ 9824.397748] PM: Entering mem sleep
Jun  7 16:40:34 kryptonite kernel: [ 9824.397770] Suspending console(s) (use no_console_suspend to debug)
Jun  7 16:40:34 kryptonite kernel: [ 9824.928269] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jun  7 16:40:34 kryptonite kernel: [ 9825.936616] sd 0:0:0:0: [sda] Stopping disk
Jun  7 16:40:34 kryptonite kernel: [ 9826.365225] parport_pc 00:0c: disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.366511] serial 00:0b: disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.488091] ipw2100 0000:02:03.0: PCI INT A disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.504465] Intel ICH 0000:00:1f.5: PCI INT B disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.504606] ata_piix 0000:00:1f.1: PCI INT A disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.504699] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Jun  7 16:40:34 kryptonite kernel: [ 9826.524715] Disabling non-boot CPUs ...
Jun  7 16:40:34 kryptonite kernel: [ 9826.524715] Back to C!
Jun  7 16:40:34 kryptonite kernel: [ 9826.525916] ACPI: Waking up from system sleep state S3
Jun  7 16:40:34 kryptonite kernel: [ 9827.570785] pm_op(): pci_pm_resume+0x0/0x70 returns -16
Jun  7 16:40:34 kryptonite kernel: [ 9827.570788] PM: Device 0000:00:00.0 failed to resume: error -16
Jun  7 16:40:34 kryptonite kernel: [ 9827.570798] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2a0c0c0, writing 0x22a0c0c0)
Jun  7 16:40:34 kryptonite kernel: [ 9827.570819] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jun  7 16:40:34 kryptonite kernel: [ 9827.570824] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  7 16:40:34 kryptonite kernel: [ 9827.570864] usb usb2: root hub lost power or was reset
Jun  7 16:40:34 kryptonite kernel: [ 9827.570881] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
Jun  7 16:40:34 kryptonite kernel: [ 9827.570886] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun  7 16:40:34 kryptonite kernel: [ 9827.570892] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun  7 16:40:34 kryptonite kernel: [ 9827.570898] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)

I'm starting to think the hard drive as is is fine, and that the kernel/filesystem is acting strange, but don't have any clues or obvious (to me) things to check at this point.  Any ideas??

---

### Post by Ocxic on 2009-06-08
when you say "built in memory checks" don't find anything, that means you have actually tested the memory with memtest right? The post test will usually miss errors that memtest will pickup.

---

### Post by z4r4thustr4 on 2009-06-08
Sorry, yes, memtest86+.

The syslog seems to indicate that the kernel put the memory to sleep, but I haven't the foggiest as to why.

---

