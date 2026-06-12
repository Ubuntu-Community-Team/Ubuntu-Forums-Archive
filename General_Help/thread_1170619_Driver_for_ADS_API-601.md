---
title: "Driver for ADS API-601"
date: 2009-05-26
forum: General Help
---

### Post by KH510 on 2009-05-26
I am trying to capture mini DV video on my laptop using an ADS Technologies IEEE1394 to CardBus Interface PC Card (part number API-601.)  I can't find a driver for it.

I am running Jaunty on my Inspiron 600m

Thanks.

---

### Post by Taxman415a on 2009-05-26
Can you eject the card, then reinsert it and post the output of the following entered into a terminal:
dmesg |tail -n 20
That can tell us if Ubuntu is recognizing the card at all. Honestly after that I don't know how to interact with your device, but it's a start.

---

### Post by KH510 on 2009-06-11
Output below:

kedron@kedron-laptop:~$ dmesg |tail -n 20
[ 4548.715500] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4548.715505]  sdb: sdb1
[ 4548.723943] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 4548.724327] sd 2:0:0:0: Attached scsi generic sg2 type 0
[13623.137240] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[13623.176841] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[000000000001b711]
[13623.180016] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[13623.280488] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[13648.021316] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[13648.021375] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[13648.021388] pci 0000:03:00.0: reg 14 32bit mmio: [0x000000-0x003fff]
[13648.021401] pci 0000:03:00.0: reg 18 32bit mmio: [0x000000-0x0007ff]
[13648.021451] pci 0000:03:00.0: supports D1 D2
[13648.021456] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[13648.021465] pci 0000:03:00.0: PME# disabled
[13648.022424] ohci1394 0000:03:00.0: enabling device (0000 -> 0002)
[13648.022443] ohci1394 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[13648.022456] ohci1394 0000:03:00.0: setting latency timer to 64
[13648.072382] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[3c004000-3c0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[13649.382797] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000000001b711]

Thanks for looking into this.

---

