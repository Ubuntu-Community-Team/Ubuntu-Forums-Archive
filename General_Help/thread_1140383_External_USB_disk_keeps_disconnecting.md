---
title: "External USB disk keeps disconnecting"
date: 2009-04-27
forum: General Help
---

### Post by krippa on 2009-04-27
I have been having some trouble lately on my old hp laptop with an external USB disk that keeps disconnecting. I have recently updated to Jaunty but I am quite sure this problem was present in Hardy as well. The problem is that after a while my external USB disk disconnects (my usb mouse connected to the same hub also gets disconnected). Yes, I have tried two different hubs, and I can't try another USB port because the other two are broken =/ It does not seem related to disk activity since it often disconnects while in use. The log shows some strange printouts every 1 second: 

Apr 27 23:10:50 k-laptop kernel: [ 4816.840052] usb 2-2: new full speed USB device using uhci_hcd and address 87
Apr 27 23:10:51 k-laptop kernel: [ 4817.560050] usb 2-2: new full speed USB device using uhci_hcd and address 88
Apr 27 23:10:51 k-laptop kernel: [ 4818.108076] usb 2-2: new full speed USB device using uhci_hcd and address 89
Apr 27 23:10:52 k-laptop kernel: [ 4818.820051] usb 2-2: new full speed USB device using uhci_hcd and address 90
Apr 27 23:10:53 k-laptop kernel: [ 4819.548062] usb 2-2: new full speed USB device using uhci_hcd and address 91
Apr 27 23:10:53 k-laptop kernel: [ 4820.316090] usb 2-2: new full speed USB device using uhci_hcd and address 92
Apr 27 23:10:54 k-laptop kernel: [ 4821.280103] usb 2-2: new full speed USB device using uhci_hcd and address 93
Apr 27 23:10:55 k-laptop kernel: [ 4821.828055] usb 2-2: new full speed USB device using uhci_hcd and address 94
Apr 27 23:10:56 k-laptop kernel: [ 4822.776082] usb 2-2: new full speed USB device using uhci_hcd and address 95
Apr 27 23:10:57 k-laptop kernel: [ 4823.552056] usb 2-2: new full speed USB device using uhci_hcd and address 96
Apr 27 23:10:57 k-laptop kernel: [ 4824.256083] usb 2-2: new full speed USB device using uhci_hcd and address 97
Apr 27 23:10:58 k-laptop kernel: [ 4824.837303] usb 2-2: new full speed USB device using uhci_hcd and address 98
Apr 27 23:10:59 k-laptop kernel: [ 4825.500056] usb 2-2: new full speed USB device using uhci_hcd and address 99
Apr 27 23:10:59 k-laptop kernel: [ 4826.277787] usb 2-2: new full speed USB device using uhci_hcd and address 100
Apr 27 23:11:00 k-laptop kernel: [ 4827.244082] usb 2-2: new full speed USB device using uhci_hcd and address 101
Apr 27 23:11:01 k-laptop kernel: [ 4827.988048] usb 2-2: new full speed USB device using uhci_hcd and address 102
Apr 27 23:11:02 k-laptop kernel: [ 4828.724069] usb 2-2: new full speed USB device using uhci_hcd and address 103
Apr 27 23:11:03 k-laptop kernel: [ 4829.472067] usb 2-2: new full speed USB device using uhci_hcd and address 104
Apr 27 23:11:03 k-laptop kernel: [ 4830.228075] usb 2-2: new full speed USB device using uhci_hcd and address 105
Apr 27 23:11:04 k-laptop kernel: [ 4831.200084] usb 2-2: new full speed USB device using uhci_hcd and address 106
Apr 27 23:11:05 k-laptop kernel: [ 4831.745806] usb 2-2: new full speed USB device using uhci_hcd and address 107
Apr 27 23:11:06 k-laptop kernel: [ 4832.700034] usb 2-2: new full speed USB device using uhci_hcd and address 108
Apr 27 23:11:06 k-laptop kernel: [ 4833.432080] usb 2-2: new full speed USB device using uhci_hcd and address 109

Any ideas?

---

