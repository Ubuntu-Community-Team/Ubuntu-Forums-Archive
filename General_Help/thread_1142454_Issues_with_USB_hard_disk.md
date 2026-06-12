---
title: "Issues with USB hard disk"
date: 2009-04-29
forum: General Help
---

### Post by vkamalaraj on 2009-04-29
Hi,

The following is from /var/log/messages when I plug in a USB Mass storage device. Is there any way to make this disk usable again? I do not need the data in the disk, just want to use the space again:

Apr 29 05:56:24 koodu kernel: [84046.750808] usb 1-7: USB disconnect, address 3
Apr 29 05:56:33 koodu kernel: [84055.716090] usb 1-7: new high speed USB device using ehci_hcd and address 4
Apr 29 05:56:33 koodu kernel: [84055.857206] usb 1-7: configuration #1 chosen from 1 choice
Apr 29 05:56:33 koodu kernel: [84055.861462] scsi4 : SCSI emulation for USB Mass Storage devices
Apr 29 05:56:38 koodu kernel: [84060.860852] scsi 4:0:0:0: Direct-Access     SEAGATE  ST3250823A       3.03 PQ: 0 ANSI: 2
Apr 29 05:56:38 koodu kernel: [84060.862167] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Apr 29 05:56:38 koodu kernel: [84060.862912] sd 4:0:0:0: [sdb] Write Protect is off
Apr 29 05:56:38 koodu kernel: [84060.863914] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Apr 29 05:56:38 koodu kernel: [84060.865679] sd 4:0:0:0: [sdb] Write Protect is off
Apr 29 05:56:48 koodu kernel: [84060.865714]  sdb:<6>sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:56:48 koodu kernel: [84070.657521] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
Apr 29 05:56:58 koodu kernel: [84080.433203] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:56:58 koodu kernel: [84080.433218] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
Apr 29 05:57:08 koodu kernel: [84090.225520] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:57:08 koodu kernel: [84090.225536] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
Apr 29 05:57:18 koodu kernel: [84100.017702] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:57:18 koodu kernel: [84100.017717] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
Apr 29 05:57:27 koodu kernel: [84109.809998] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:57:27 koodu kernel: [84109.810008] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
Apr 29 05:57:37 koodu kernel: [84119.594094] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Apr 29 05:57:37 koodu kernel: [84119.594109] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Logical unit not ready, cause not reportable


Thanks in Advance,
Vinod

---

### Post by Bindsa on 2009-04-29
Make sure you removed your disk safely when you plugged it into windows the last time, if you haven't got access to Windows then try to force mount it.

---

