---
title: "HAL bug or kernel bug: removing a card vs removing a usb stick"
date: 2006-07-09
forum: Desktop Environments
---

### Post by bogolisk on 2006-07-09
when I insert a usb stick or a card into my card-reader, a new icon for the card/drive will appear on the desktop.

Removing the usb stick will also make the icon disappear.

On the other hand, removing the card from the card reader doesn't seems to notify hal/dbus/gnome/desktop. The icon is still on the Desktop and the gnome will get confused if you try to browse the (removed) card. The kernel doesn't seem to have/produce an event for the card removal.

Is it a bug with the kernel or hal?

syslog when insert/remove usb drive
```

Jul  9 20:39:10 hanhi kernel: [17365673.132000] usb 2-8: new high speed USB device using ehci_hcd and address 4
Jul  9 20:39:10 hanhi kernel: [17365673.268000] scsi5 : SCSI emulation for USB Mass Storage devices
Jul  9 20:39:10 hanhi kernel: [17365673.268000] usb-storage: device found at 4
Jul  9 20:39:10 hanhi kernel: [17365673.268000] usb-storage: waiting for device to settle before scanning
Jul  9 20:39:15 hanhi kernel: [17365678.268000]   Vendor: Multi     Model: Flash Reader      Rev: 1.00
Jul  9 20:39:15 hanhi kernel: [17365678.268000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul  9 20:39:16 hanhi kernel: [17365678.824000] SCSI device sdf: 1002496 512-byte hdwr sectors (513 MB)
Jul  9 20:39:16 hanhi kernel: [17365678.828000] sdf: Write Protect is off
Jul  9 20:39:16 hanhi kernel: [17365678.828000] sdf: Mode Sense: 03 00 00 00
Jul  9 20:39:16 hanhi kernel: [17365678.828000] sdf: assuming drive cache: write through
Jul  9 20:39:16 hanhi kernel: [17365678.832000] SCSI device sdf: 1002496 512-byte hdwr sectors (513 MB)
Jul  9 20:39:16 hanhi kernel: [17365678.836000] sdf: Write Protect is off
Jul  9 20:39:16 hanhi kernel: [17365678.836000] sdf: Mode Sense: 03 00 00 00
Jul  9 20:39:16 hanhi kernel: [17365678.836000] sdf: assuming drive cache: write through
Jul  9 20:39:16 hanhi kernel: [17365678.836000]  sdf: sdf1
Jul  9 20:39:16 hanhi kernel: [17365678.840000] sd 5:0:0:0: Attached scsi removable disk sdf
Jul  9 20:39:16 hanhi kernel: [17365678.840000] sd 5:0:0:0: Attached scsi generic sg5 type 0
Jul  9 20:39:16 hanhi kernel: [17365678.840000] usb-storage: device scan complete
Jul  9 20:39:16 hanhi kernel: [17365679.292000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Jul  9 20:39:21 hanhi kernel: [17365683.980000] usb 2-8: USB disconnect, address 4

```

syslog when insert/remove card into/from reader
```

Jul  9 20:39:43 hanhi kernel: [17365706.516000] ready
Jul  9 20:39:43 hanhi kernel: [17365706.516000] SCSI device sdb: 500736 512-byte hdwr sectors (256 MB)
Jul  9 20:39:43 hanhi kernel: [17365706.524000] sdb: Write Protect is off
Jul  9 20:39:43 hanhi kernel: [17365706.524000] sdb: Mode Sense: 23 00 00 00
Jul  9 20:39:43 hanhi kernel: [17365706.524000] sdb: assuming drive cache: write through
Jul  9 20:39:43 hanhi kernel: [17365706.532000] SCSI device sdb: 500736 512-byte hdwr sectors (256 MB)
Jul  9 20:39:43 hanhi kernel: [17365706.540000] sdb: Write Protect is off
Jul  9 20:39:43 hanhi kernel: [17365706.540000] sdb: Mode Sense: 23 00 00 00
Jul  9 20:39:43 hanhi kernel: [17365706.540000] sdb: assuming drive cache: write through
Jul  9 20:39:43 hanhi kernel: [17365706.540000]  sdb: sdb1
Jul  9 20:39:44 hanhi kernel: [17365706.784000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

