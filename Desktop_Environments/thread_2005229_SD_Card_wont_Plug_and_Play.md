---
title: "SD Card wont Plug and Play"
date: 2012-06-17
forum: Desktop Environments
---

### Post by Geffers on 2012-06-17
Ubuntu V 12.04

For some reason memory cards will not plug and play in my HP Pavilion laptop, I had the same problem with previous versions of Ubuntu.

If I insert a card before switching on it is recognised and any subsequent unmounting and mounting works.

I have tried to view the syslog and have tried sudo modprobe pata_atiixp but that didn't appear to work.

The following is the output of the section of syslog that hopefully applies to the memory card;

> Jun 17 11:26:37 mercury kernel: [    2.199968] sdhci: Secure Digital Host Controller Interface driver
Jun 17 11:26:37 mercury kernel: [    2.199971] sdhci: Copyright(c) Pierre Ossman
Jun 17 11:26:37 mercury kernel: [    2.221771] scsi3 : pata_atiixp
Jun 17 11:26:37 mercury kernel: [    2.224452] scsi4 : pata_atiixp
Jun 17 11:26:37 mercury kernel: [    2.225133] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6000 irq 14
Jun 17 11:26:37 mercury kernel: [    2.225137] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6008 irq 15
Jun 17 11:26:37 mercury kernel: [    2.260128] firewire_ohci: Added fw-ohci device 0000:0a:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
Jun 17 11:26:37 mercury kernel: [    2.260192] sdhci-pci 0000:0a:00.1: SDHCI controller found [197b:2382] (rev 0)
Jun 17 11:26:37 mercury kernel: [    2.260218] sdhci-pci 0000:0a:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 17 11:26:37 mercury kernel: [    2.260309] sdhci-pci 0000:0a:00.1: setting latency timer to 64
Jun 17 11:26:37 mercury kernel: [    2.260327] mmc0: no vmmc regulator found
Jun 17 11:26:37 mercury kernel: [    2.260381] Registered led device: mmc0::
Jun 17 11:26:37 mercury kernel: [    2.261435] mmc0: SDHCI controller on PCI [0000:0a:00.1] using DMA
Jun 17 11:26:37 mercury kernel: [    2.261479] sdhci-pci 0000:0a:00.2: SDHCI controller found [197b:2381] (rev 0)
Jun 17 11:26:37 mercury kernel: [    2.261492] sdhci-pci 0000:0a:00.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 17 11:26:37 mercury kernel: [    2.261503] sdhci-pci 0000:0a:00.2: Refusing to bind to secondary interface.
Jun 17 11:26:37 mercury kernel: [    2.261511] sdhci-pci 0000:0a:00.2: PCI INT A disabled
Jun 17 11:26:37 mercury kernel: [    2.344858] mmc0: new SD card at address 13f1
Jun 17 11:26:37 mercury kernel: [    2.385271] mmcblk0: mmc0:13f1 SD02G 1.83 GiB 
Jun 17 11:26:37 mercury kernel: [    2.386390]  mmcblk0: p1

Appreciate any advice to resolve this please.

Geffers

---

### Post by mbuell on 2012-06-17
You may have already been through the following, but just in case, 

[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by Geffers on 2012-06-17
> **mbuell said:**
> You may have already been through the following, but just in case, 

[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

Thanks for suggestion but the device is not even showing on system logs as being inserted.

Geffers

---

### Post by Geffers on 2012-06-18
Purely by accident this has been solved.

Checking BIOS for an unconnected reason I noticed the card reader was in power save mode, turned this off and now works fine.

Geffers

---

