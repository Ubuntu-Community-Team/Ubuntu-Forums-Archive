---
title: "USB 2.0 Problems"
date: 2011-10-23
forum: Desktop Environments
---

### Post by ssss25 on 2011-10-23
Hi,

I have got A Dell Precision 380, running ubuntu Lucid. All works well except for USB!

I have a USB keyboard and mouse, printer and they are 1.1 devices.

I also have a USB drive and a DVB card,which are USB 2.0.

After a random number of hours, I lose the USB 2,0 stuff. At first I See:


ssss@SRV:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b8:083f Seiko Epson Corp. Stylus DX4450
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 059b:0577 Iomega Corp. 
Bus 001 Device 004: ID 09c0:0203  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

after failure, I don't see any USB stuff:

shadi@SRV:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b8:083f Seiko Epson Corp. Stylus DX4450
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Dmesg shows me crashes all over:

```
Oct 13 06:38:57 SRV kernel: [85823.175893] usb 1-2: USB disconnect, address 3
Oct 13 06:38:57 SRV kernel: [85823.175917] gp8psk: usb out operation failed.
Oct 13 06:38:57 SRV kernel: [85823.176404] gp8psk: usb out operation failed.
Oct 13 06:38:57 SRV kernel: [85823.179880] gp8psk: usb in 144 operation failed.
Oct 13 06:38:57 SRV kernel: [85823.179885] gp8psk: usb in 135 operation failed.
Oct 13 06:38:57 SRV kernel: [85823.191945] usb 1-5: USB disconnect, address 4
Oct 13 06:38:57 SRV kernel: [85823.204762] usb 1-7: USB disconnect, address 5
Oct 13 06:38:57 SRV kernel: [85823.205013] gp8psk: usb out operation failed.
Oct 13 06:38:57 SRV kernel: [85823.205018] gp8psk: usb in 138 operation failed.
Oct 13 06:42:35 SRV kernel: [86041.056034] khubd         D 000214f6     0    29      2 0x00000000
Oct 13 06:42:35 SRV kernel: [86041.056042]  f74d7df8 00000046 eea86000 000214f6 00000000 c088e5c0 f7527564 c088e5c0
Oct 13 06:42:35 SRV kernel: [86041.056055]  45e250f7 00004e0e c088e5c0 c088e5c0 f7527564 c088e5c0 c088e5c0 f21cec00
Oct 13 06:42:35 SRV kernel: [86041.056067]  00000001 00004e0e f75272c0 efbf7c00 f74d7e08 ee148918 f74d7e24 f82b1cc5
Oct 13 06:42:35 SRV kernel: [86041.056080] Call Trace:
Oct 13 06:42:35 SRV kernel: [86041.056103]  [<f82b1cc5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
Oct 13 06:42:35 SRV kernel: [86041.056114]  [<c01709e0>] ? autoremove_wake_function+0x0/0x50
Oct 13 06:42:35 SRV kernel: [86041.056122]  [<f82a226b>] dvb_usb_adapter_frontend_exit+0x3b/0x70 [dvb_usb]
Oct 13 06:42:35 SRV kernel: [86041.056129]  [<f82a150a>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
Oct 13 06:42:35 SRV kernel: [86041.056137]  [<c046eade>] ? usb_disable_endpoint+0x4e/0x80
Oct 13 06:42:35 SRV kernel: [86041.056145]  [<f82a15f2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
Oct 13 06:42:35 SRV kernel: [86041.056150]  [<c0471e29>] usb_unbind_interface+0xe9/0x130
Oct 13 06:42:35 SRV kernel: [86041.056158]  [<c03fdd91>] __device_release_driver+0x51/0xb0
Oct 13 06:42:35 SRV kernel: [86041.056164]  [<c03fdeb5>] device_release_driver+0x25/0x40
Oct 13 06:42:35 SRV kernel: [86041.056170]  [<c03fd16b>] bus_remove_device+0x7b/0xa0
Oct 13 06:42:35 SRV kernel: [86041.056175]  [<c03fb5e7>] device_del+0xf7/0x180
Oct 13 06:42:35 SRV kernel: [86041.056181]  [<c046eb73>] usb_disable_device+0x63/0x110
Oct 13 06:42:35 SRV kernel: [86041.056186]  [<c046958e>] usb_disconnect+0x9e/0x120
Oct 13 06:42:35 SRV kernel: [86041.056192]  [<c046965f>] hub_quiesce+0x4f/0x90
Oct 13 06:42:35 SRV kernel: [86041.056197]  [<c046a940>] hub_events+0x20/0x520
Oct 13 06:42:35 SRV kernel: [86041.056204]  [<c05b0eab>] ? schedule+0x46b/0x870
Oct 13 06:42:35 SRV kernel: [86041.056210]  [<c05b2fbf>] ? _spin_lock_irqsave+0x2f/0x50
Oct 13 06:42:35 SRV kernel: [86041.056215]  [<c0170b4f>] ? finish_wait+0x4f/0x70
Oct 13 06:42:35 SRV kernel: [86041.056221]  [<c046ae7a>] hub_thread+0x3a/0x140
Oct 13 06:42:35 SRV kernel: [86041.056226]  [<c01709e0>] ? autoremove_wake_function+0x0/0x50
Oct 13 06:42:35 SRV kernel: [86041.056232]  [<c046ae40>] ? hub_thread+0x0/0x140
Oct 13 06:42:35 SRV kernel: [86041.056236]  [<c0170754>] kthread+0x74/0x80
Oct 13 06:42:35 SRV kernel: [86041.056241]  [<c01706e0>] ? kthread+0x0/0x80
Oct 13 06:42:35 SRV kernel: [86041.056247]  [<c010a447>] kernel_thread_helper+0x7/0x10
Oct 13 06:44:35 SRV kernel: [86161.056033] khubd         D 000214f6     0    29      2 0x00000000
Oct 13 06:44:35 SRV kernel: [86161.056042]  f74d7df8 00000046 eea86000 000214f6 00000000 c088e5c0 f7527564 c088e5c0
Oct 13 06:44:35 SRV kernel: [86161.056055]  45e250f7 00004e0e c088e5c0 c088e5c0 f7527564 c088e5c0 c088e5c0 f21cec00
Oct 13 06:44:35 SRV kernel: [86161.056067]  00000001 00004e0e f75272c0 efbf7c00 f74d7e08 ee148918 f74d7e24 f82b1cc5
Oct 13 06:44:35 SRV kernel: [86161.056080] Call Trace:
Oct 13 06:44:35 SRV kernel: [86161.056103]  [<f82b1cc5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
Oct 13 06:44:35 SRV kernel: [86161.056113]  [<c01709e0>] ? autoremove_wake_function+0x0/0x50
Oct 13 06:44:35 SRV kernel: [86161.056123]  [<f82a226b>] dvb_usb_adapter_frontend_exit+0x3b/0x70 [dvb_usb]
Oct 13 06:44:35 SRV kernel: [86161.056130]  [<f82a150a>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
Oct 13 06:44:35 SRV kernel: [86161.056138]  [<c046eade>] ? usb_disable_endpoint+0x4e/0x80
Oct 13 06:44:35 SRV kernel: [86161.056146]  [<f82a15f2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
Oct 13 06:44:35 SRV kernel: [86161.056152]  [<c0471e29>] usb_unbind_interface+0xe9/0x130
```

The only way I know to get back my drive and DVB device is to restart!!

Any help?? I disconnected drive and left DVB device only, it also fails, but it takes more time... 

Any ideas? Any knows bugs for USB 2.0 in Lucid?

Should I just accept the fact and do a restart every 24 hours to try to avoid this?

Thanks for any help.

---

### Post by ssss25 on 2012-02-28
Solved by buying a cheap USB adapter card.

---

