---
title: "Ubuntu Freezing"
date: 2006-04-28
forum: Desktop Environments
---

### Post by kaptainlange on 2006-04-28
I'm not sure if this is the correct forum, as I am using an AMD 64, but I am not using the 64-bit kernel, using 2.6.12-10-k7.

Here is the problem, Ubuntu freezes on my girlfriend's desktop.  It happens at startup.  GDM will come up and act as if everything is fine, however the keyboard and mouse don't work.  I cannot toggle numlock status, and the mouse's laser is continuously lit.  So I am unsure if the entire system is freezing or if just those inputs are not responding.  Normally pressing the system's power button initializes a shutdown in Linux, however it does not work when this happens.

This problem is not 100% predictable.  It happens maybe 75% of the time.  The times it boots up, it is completely fine.  The computer runs without a hitch.  As such I've been checking logs.  Here's a discrepency I noticed in the kernel log.

This is a boot where it freezes
```
Apr 28 18:32:51 localhost kernel: Inspecting /boot/System.map-2.6.12-10-k7
Apr 28 18:32:51 localhost kernel: Loaded 28252 symbols from /boot/System.map-2.6.12-10-k7.
Apr 28 18:32:51 localhost kernel: Symbols match kernel version 2.6.12.
Apr 28 18:32:51 localhost kernel: No module symbols loaded - kernel modules not enabled.
Apr 28 18:32:51 localhost kernel: IOS revision 3.00 entry at 0xfb400, last bus=5
Apr 28 18:32:51 localhost kernel: [4294669.116000] PCI: Using configuration type 1
Apr 28 18:32:51 localhost kernel: [4294669.116000] mtrr: v2.0 (20020519)
Apr 28 18:32:51 localhost kernel: [4294669.117000] ACPI: Subsystem revision 20050729
Apr 28 18:32:51 localhost kernel: [4294669.125000] ACPI: Interpreter enabled
Apr 28 18:32:51 localhost kernel: [4294669.125000] ACPI: Using IOAPIC for interrupt routing
Apr 28 18:32:51 localhost kernel: [4294669.125000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 28 18:32:51 localhost kernel: [4294669.125000] PCI: Probing PCI hardware (bus 00)
Apr 28 18:32:51 localhost kernel: [4294669.125000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
Apr 28 18:32:51 localhost kernel: [4294669.128000] PCI: Transparent bridge - 0000:00:09.0
Apr 28 18:32:51 localhost kernel: [4294669.128000] Boot video device is 0000:05:00.0
Apr 28 18:32:51 localhost kernel: [4294669.185000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

```

This is a boot that goes fine
```
Apr 28 18:34:04 localhost kernel: Inspecting /boot/System.map-2.6.12-10-k7
Apr 28 18:34:04 localhost kernel: Loaded 28252 symbols from /boot/System.map-2.6.12-10-k7.
Apr 28 18:34:04 localhost kernel: Symbols match kernel version 2.6.12.
Apr 28 18:34:04 localhost kernel: No module symbols loaded - kernel modules not enabled.
Apr 28 18:34:04 localhost kernel: 4294671.958000] ACPI: Interpreter enabled
Apr 28 18:34:04 localhost kernel: [4294671.958000] ACPI: Using IOAPIC for interrupt routing
Apr 28 18:34:04 localhost kernel: [4294671.958000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 28 18:34:04 localhost kernel: [4294671.958000] PCI: Probing PCI hardware (bus 00)
Apr 28 18:34:04 localhost kernel: [4294671.958000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
Apr 28 18:34:04 localhost kernel: [4294671.961000] PCI: Transparent bridge - 0000:00:09.0
Apr 28 18:34:04 localhost kernel: [4294671.961000] Boot video device is 0000:05:00.0
Apr 28 18:34:04 localhost kernel: [4294672.018000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

```

From then on everything appears to be the same.

Any insight would be appreciated, also let me know what outputs might help you diagnose this problem better.

---

### Post by Ramses de Norre on 2006-04-28
Have seen this problem with amd64 and ati cards which used the ati driver. If this is the case: try the fglrx driver.

---

### Post by kaptainlange on 2006-04-28
That's not it, using a GeForce 6600 with the proprietary Nvidia driver.  Also, this problem appears to occur before any drivers are loaded.  I am not 100 percent sure on that though.

---

### Post by psycardis on 2007-08-26
I have this exact problem and I am running the same video card with proprietary drivers, intel chipset though. Any help would be appreciated. Unfortunately sometimes it does it at random while the system is running.

---

