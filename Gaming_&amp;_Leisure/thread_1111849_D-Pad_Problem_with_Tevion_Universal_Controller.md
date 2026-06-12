---
title: "D-Pad Problem with Tevion Universal Controller"
date: 2009-03-31
forum: Gaming &amp; Leisure
---

### Post by wubifun on 2009-03-31
I recently bought a second-hand controller which has USB, PSX and (I think) X-Box connections. Although it was recognized perfectly and most of the buttons + both analog controls work, but I cannot get the D-Pad to work. I even tried doing a "cat /dev/input/js0" and could not see anything when I used the D-Pad (though all the other buttons produced output.)

Here is the output of dmesg when I  plug it in:
```
[ 1381.792047] usb 3-1: new full speed USB device using ohci_hcd and address 4
[ 1382.004287] usb 3-1: configuration #1 chosen from 1 choice
[ 1382.012519] hub 3-1:1.0: USB hub found
[ 1382.014264] hub 3-1:1.0: 3 ports detected
[ 1382.324024] eth0: auto-negotiating...
[ 1382.326109] usb 3-1.1: new full speed USB device using ohci_hcd and address 5
[ 1382.436337] usb 3-1.1: configuration #1 chosen from 1 choice
[ 1382.453187] input: Jess Technology Co., Ltd. USB Game Controller as /devices/pci0000:00/0000:00:03.1/usb3/3-1/3-1.1/3-1.1:1.0/input/input10
[ 1382.480228] input,hidraw0: USB HID v1.01 Joystick [Jess Technology Co., Ltd. USB Game Controller] on usb-0000:00:03.1-1.1

```

and lsusb:
```

Bus 003 Device 005: ID 22ba:1020 Technology Innovation Holdings, Ltd
Bus 003 Device 004: ID 0f30:001c Jess Technology Co., Ltd PS3 Guitar Controller Dongle
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

NB: For some reason it is shown as a PS3 guitar controller dongle.

---

