---
title: "USB drives stoped working"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Hellcom on 2006-07-18
Well I just upgraded to 6.06, and everything worked fine for a while. However, unbuntu now refuses to detect any external storage via usb.

I have one usb flash drive formatted FAT32 and a HDD enclosure with a HD formatted NTFS.

lsusb
Bus 002 Device 003: ID 06a3:8020 Saitek PLC
Bus 002 Device 002: ID 046d:c01d Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by Hellcom on 2006-07-18
sudo tail -f /var/log/messages

> Jul 18 07:37:53 localhost kernel: [17181154.172000] usb 1-4: new high speed USB device using ehci_hcd and address 113
Jul 18 07:38:04 localhost kernel: [17181165.828000] usb 1-4: new high speed USB device using ehci_hcd and address 114
Jul 18 07:38:16 localhost kernel: [17181177.484000] usb 1-4: new high speed USB device using ehci_hcd and address 115
Jul 18 07:38:26 localhost kernel: [17181188.020000] usb 1-4: new high speed USB device using ehci_hcd and address 116
Jul 18 07:38:37 localhost kernel: [17181198.772000] usb 1-4: new high speed USB device using ehci_hcd and address 117
Jul 18 07:38:49 localhost kernel: [17181210.428000] usb 1-4: new high speed USB device using ehci_hcd and address 118
Jul 18 07:39:00 localhost kernel: [17181222.088000] usb 1-4: new high speed USB device using ehci_hcd and address 119
Jul 18 07:39:11 localhost kernel: [17181232.628000] usb 1-4: new high speed USB device using ehci_hcd and address 120


---

