---
title: "Strange I/O errors in dmesg"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Silverstar on 2005-11-10
Hello,

I've got a strange problem with my SATA harddrive. When I open a console and run dmesg | grep sda, it tells me the following:

[4294688.868000] sda: Current: sense key: Hardware Error
[4294688.868000] end_request: I/O error, dev sda, sector 50831338
[4294694.192000] sda: Current: sense key: Hardware Error
[4294694.192000] end_request: I/O error, dev sda, sector 51194570
[4294696.382000] sda: Current: sense key: Hardware Error
[4294696.382000] end_request: I/O error, dev sda, sector 19140034
[4298495.263000] sda: Current: sense key: Hardware Error
[4298495.263000] end_request: I/O error, dev sda, sector 21329602
[4298495.271000] sda: Current: sense key: Hardware Error
[4298495.271000] end_request: I/O error, dev sda, sector 21354682

As you can see, there are not many errors. I don't know where they come from, because it seems that the drive is working properly. lspci says that the SATA controller is recognized and that the driver is loaded, so that can't be the problem I think:

[4294673.930000] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x9402 bmdma 0xA000 irq 20
[4294673.930000] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9C02 bmdma 0xA008 irq 20

The harddrive is tested and completed without errors.

Does anyone know how I can get off these error messages?

---

### Post by Silverstar on 2005-11-12
Kick

---

