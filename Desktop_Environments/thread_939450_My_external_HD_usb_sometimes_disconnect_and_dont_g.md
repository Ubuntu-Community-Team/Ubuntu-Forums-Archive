---
title: "My external HD usb sometimes disconnect and dont get detected again"
date: 2008-10-05
forum: Desktop Environments
---

### Post by hecato on 2008-10-05
Hi there, I ahve an external HD that I connect via USB.

The connector have a little problem, is a false contact, which affects that sometimes when I move the HD it gets disconnected and then connected.


The problem come that when it get connected again, it is not mounted and I dont know how to mount it again, thus Im unable to see again my files until I reboot the system again.


This is my last dmesg:

```

[   86.893562] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   87.027086] usb 7-2: configuration #1 chosen from 1 choice
[   87.192917] usbcore: registered new interface driver libusual
[   87.237366] Initializing USB Mass Storage driver...
[   87.247367] scsi5 : SCSI emulation for USB Mass Storage devices
[   87.250233] usbcore: registered new interface driver usb-storage
[   87.250240] USB Mass Storage support registered.
[   87.250653] usb-storage: device found at 2
[   87.250657] usb-storage: waiting for device to settle before scanning
[   91.955057] usb-storage: device scan complete
[   91.955646] scsi 5:0:0:0: Direct-Access     FUJITSU  MHV2100AH        0014 PQ: 0 ANSI: 0
[   91.971616] sd 5:0:0:0: [sdb] 195371568 512-byte hardware sectors (100030 MB)
[   91.972604] sd 5:0:0:0: [sdb] Write Protect is off
[   91.972609] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   91.972611] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   91.973597] sd 5:0:0:0: [sdb] 195371568 512-byte hardware sectors (100030 MB)
[   91.974722] sd 5:0:0:0: [sdb] Write Protect is off
[   91.974727] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   91.974730] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   91.974734]  sdb: sdb1
[   92.052045] sd 5:0:0:0: [sdb] Attached SCSI disk
[   92.052094] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  691.948999] usb 7-2: USB disconnect, address 2
[  692.227865] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  692.358343] usb 7-2: configuration #1 chosen from 1 choice
[  692.381336] scsi6 : SCSI emulation for USB Mass Storage devices
[  692.410647] usb-storage: device found at 3
[  692.410652] usb-storage: waiting for device to settle before scanning
[  694.543995] usb-storage: device scan complete
[  694.544659] scsi 6:0:0:0: Direct-Access     FUJITSU  MHV2100AH        0014 PQ: 0 ANSI: 0
[  694.551610] sd 6:0:0:0: [sdc] 195371568 512-byte hardware sectors (100030 MB)
[  694.552855] sd 6:0:0:0: [sdc] Write Protect is off
[  694.552863] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  694.552868] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  694.554853] sd 6:0:0:0: [sdc] 195371568 512-byte hardware sectors (100030 MB)
[  694.556103] sd 6:0:0:0: [sdc] Write Protect is off
[  694.556110] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  694.556115] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  694.556121]  sdc: sdc1
[  694.808580] sd 6:0:0:0: [sdc] Attached SCSI disk
[  694.808669] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  695.508699] usb 7-2: USB disconnect, address 3
[  695.664645] usb 7-2: new high speed USB device using ehci_hcd and address 4
[  710.167428] usb 7-2: new high speed USB device using ehci_hcd and address 5
[  710.283705] usb 7-2: configuration #1 chosen from 1 choice
[  710.300961] scsi7 : SCSI emulation for USB Mass Storage devices
[  710.304138] usb-storage: device found at 5
[  710.304146] usb-storage: waiting for device to settle before scanning
[  712.212293] usb-storage: device scan complete
[  712.213102] scsi 7:0:0:0: Direct-Access     FUJITSU  MHV2100AH        0014 PQ: 0 ANSI: 0
[  712.220113] sd 7:0:0:0: [sdc] 195371568 512-byte hardware sectors (100030 MB)
[  712.221614] sd 7:0:0:0: [sdc] Write Protect is off
[  712.221622] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  712.221627] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  712.223610] sd 7:0:0:0: [sdc] 195371568 512-byte hardware sectors (100030 MB)
[  712.224862] sd 7:0:0:0: [sdc] Write Protect is off
[  712.224868] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  712.224873] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  712.224879]  sdc: sdc1
[  712.301925] sd 7:0:0:0: [sdc] Attached SCSI disk
[  712.301975] sd 7:0:0:0: Attached scsi generic sg2 type 0

```

---

