---
title: "Flash Drive won't mount"
date: 2006-07-04
forum: Desktop Environments
---

### Post by ColonelDimak on 2006-07-04
My flash drive is failing to mount once i plug it in. I checked the other threads i could find on the issue but I was unable to get those methods to work. I ran desmg and got this

> [17182023.876000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17182023.876000] end_request: I/O error, dev sda, sector 0
[17182023.876000] Buffer I/O error on device sda, logical block 0
[17182023.876000] sd 2:0:0:0: rejecting I/O to offline device
[17182023.876000] Buffer I/O error on device sda, logical block 0
[17182023.876000]  unable to read partition table
[17182023.876000] sd 2:0:0:0: Attached scsi removable disk sda
[17182023.876000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17182023.888000] usb-storage: device scan complete
[17182024.000000] usb 4-4: new high speed USB device using ehci_hcd and address 19
[17182027.112000] usb 4-4: device descriptor read/64, error -110
[17182042.328000] usb 4-4: device descriptor read/64, error -110
[17182042.544000] usb 4-4: new high speed USB device using ehci_hcd and address 20
[17182045.656000] usb 4-4: device descriptor read/64, error -110
[17182060.872000] usb 4-4: device descriptor read/64, error -110
[17182061.088000] usb 4-4: new high speed USB device using ehci_hcd and address 21
[17182071.496000] usb 4-4: device not accepting address 21, error -110
[17182071.608000] usb 4-4: new high speed USB device using ehci_hcd and address 22
[17182082.016000] usb 4-4: device not accepting address 22, error -110


and then I ran $ sudo tail -f /var/log/messages and got

> Jul  4 14:46:41 stephen-laptop kernel: [17182448.532000] usb 4-4: new high speed USB device using ehci_hcd and address 23
Jul  4 14:46:41 stephen-laptop kernel: [17182448.668000] scsi3 : SCSI emulation for USB Mass Storage devices
Jul  4 14:46:46 stephen-laptop kernel: [17182453.668000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
Jul  4 14:46:46 stephen-laptop kernel: [17182453.668000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul  4 14:46:46 stephen-laptop kernel: [17182453.900000] SCSI device sda: 1965056 512-byte hdwr sectors (1006 MB)
Jul  4 14:46:46 stephen-laptop kernel: [17182453.900000] sda: Write Protect is off
Jul  4 14:46:46 stephen-laptop kernel: [17182453.904000] SCSI device sda: 1965056 512-byte hdwr sectors (1006 MB)
Jul  4 14:46:46 stephen-laptop kernel: [17182453.904000] sda: Write Protect is off
Jul  4 14:47:17 stephen-laptop kernel: [17182453.904000]  sda:<6>usb 4-4: reset high speed USB device using ehci_hcd and address 23
Jul  4 14:47:35 stephen-laptop kernel: [17182502.560000] usb 4-4: reset high speed USB device using ehci_hcd and address 23
Jul  4 14:47:54 stephen-laptop kernel: [17182521.104000] usb 4-4: reset high speed USB device using ehci_hcd and address 23
Jul  4 14:48:04 stephen-laptop kernel: [17182531.624000] usb 4-4: reset high speed USB device using ehci_hcd and address 23
Jul  4 14:48:15 stephen-laptop kernel: [17182542.032000] usb 4-4: USB disconnect, address 23
Jul  4 14:48:15 stephen-laptop kernel: [17182542.032000] sd 3:0:0:0: scsi: Device offlined - not ready after error recovery
Jul  4 14:48:15 stephen-laptop kernel: [17182542.032000] sd 3:0:0:0: SCSI error: return code = 0x50000
Jul  4 14:48:15 stephen-laptop kernel: [17182542.032000] end_request: I/O error, dev sda, sector 0
Jul  4 14:48:15 stephen-laptop kernel: [17182542.032000]  unable to read partition table
 
anyone know what this means and how to fix it?

---

