---
title: "Keyboard/Mouse receivers missing from lsusb after return from suspend in 22.04"
date: 2022-05-05
forum: Desktop Environments
---

### Post by misnoma on 2022-05-05
I ran 20.04 on this machine for over a year, and suspend/resume worked perfectly every time - then an ubuntu-provided kernel upgrade managed to cause issues with my video card on resume. Feeling brave and reading that the kernel bug had been fixed in later kernels I upgraded to 22.04 - since that seemed like a fun thing to do also :)

So - the video card issue is gone (yay) however now when my machine wakes from suspend the keyboard and mouse receivers (Logitech/Microsoft) are gone.

Before:

```
 &#10007; lsusbBus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 1050:0120 Yubico.com Yubikey Touch U2F Security Key
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 004: ID 045e:07a5 Microsoft Corp. Wireless Receiver 1461C
Bus 003 Device 003: ID 046d:c539 Logitech, Inc. USB Receiver
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1e71:2007 NZXT NZXT USB Device
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 291a:3361 Anker Anker PowerConf C300
Bus 001 Device 002: ID 048d:8297 Integrated Technology Express, Inc. IT8297 RGB LED Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

After (via ssh):

```
&#10007; lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 1050:0120 Yubico.com Yubikey Touch U2F Security Key
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1e71:2007 NZXT NZXT USB Device
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 291a:3361 Anker Anker PowerConf C300
Bus 001 Device 002: ID 048d:8297 Integrated Technology Express, Inc. IT8297 RGB LED Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I've tried unplugging/replugging the dongles into the machine to see if that wakes them up, but nothing seems to work barring a reboot. I found some stuff around unbinding/binding the devices to reset them but this requires the device to exist in lsusb from what I can tell (and from the "no such device" errors :) ).

Anyone have any clues as to how I can debug this further/wake things up? Happy to provide more output if someone can point me at useful places to look - it's easy enough to ssh into the machine even when the keyboard/mouse are non-functional.

---

### Post by ActionParsnip on 2022-05-05
After you unplug it and plug it back in, run:
```

dmesg | tail

```
What is the output please?

---

### Post by misnoma on 2022-05-05
This is before unplugging/plugging (just after waking):

```
&#10140;  ~ sudo dmesg | grep -v audit | tail -50
[ 6186.506407] [drm] PCIE GART of 512M enabled (table at 0x0000008000000000).
[ 6186.506424] [drm] PSP is resuming...
[ 6186.508783] nvme nvme0: Shutdown timeout set to 8 seconds
[ 6186.534455] nvme nvme1: 8/0/0 default/read/poll queues
[ 6186.538052] nvme nvme0: 32/0/0 default/read/poll queues
[ 6186.576302] [drm] reserve 0x900000 from 0x800f400000 for PSP TMR
[ 6186.618150] amdgpu 0000:0b:00.0: amdgpu: RAS: optional ras ta ucode is not available
[ 6186.624088] amdgpu 0000:0b:00.0: amdgpu: RAP: optional rap ta ucode is not available
[ 6186.624090] amdgpu 0000:0b:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
[ 6186.624092] amdgpu 0000:0b:00.0: amdgpu: SMU is resuming...
[ 6186.659649] amdgpu 0000:0b:00.0: amdgpu: SMU is resumed successfully!
[ 6186.791767] [drm] kiq ring mec 2 pipe 1 q 0
[ 6186.793967] [drm] VCN decode and encode initialized successfully(under DPG Mode).
[ 6186.794350] [drm] JPEG decode initialized successfully.
[ 6186.794365] amdgpu 0000:0b:00.0: amdgpu: ring gfx_0.0.0 uses VM inv eng 0 on hub 0
[ 6186.794367] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[ 6186.794368] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[ 6186.794369] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[ 6186.794369] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[ 6186.794370] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[ 6186.794370] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[ 6186.794371] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[ 6186.794372] amdgpu 0000:0b:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[ 6186.794373] amdgpu 0000:0b:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[ 6186.794373] amdgpu 0000:0b:00.0: amdgpu: ring sdma0 uses VM inv eng 12 on hub 0
[ 6186.794374] amdgpu 0000:0b:00.0: amdgpu: ring sdma1 uses VM inv eng 13 on hub 0
[ 6186.794374] amdgpu 0000:0b:00.0: amdgpu: ring vcn_dec uses VM inv eng 0 on hub 1
[ 6186.794375] amdgpu 0000:0b:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 1 on hub 1
[ 6186.794376] amdgpu 0000:0b:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 4 on hub 1
[ 6186.794376] amdgpu 0000:0b:00.0: amdgpu: ring jpeg_dec uses VM inv eng 5 on hub 1
[ 6186.799751] OOM killer enabled.
[ 6186.799752] Restarting tasks ...
[ 6186.799852] usb 3-6: USB disconnect, device number 2
[ 6186.799857] usb 3-6.1: USB disconnect, device number 3
[ 6186.807322] done.
[ 6186.807495] PM: suspend exit
[ 6186.825156] usb 3-6.2: USB disconnect, device number 4
[ 6187.331343] usb 3-6.4: USB disconnect, device number 5
[ 6187.486230] xhci_hcd 0000:06:00.3: Port resume timed out, port 3-6: 0xfe3
[ 6187.546216] usb 3-6: new high-speed USB device number 6 using xhci_hcd
[ 6189.962942] igb 0000:05:00.0 enp5s0: igb: enp5s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 6190.070846] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
[ 6193.842777] igb 0000:05:00.0 enp5s0: igb: enp5s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[ 6197.922012] xhci_hcd 0000:06:00.3: xHCI host not responding to stop endpoint command.
[ 6197.922019] xhci_hcd 0000:06:00.3: USBSTS:
[ 6197.937921] xhci_hcd 0000:06:00.3: xHCI host controller not responding, assume dead
[ 6197.937930] xhci_hcd 0000:06:00.3: HC died; cleaning up
[ 6197.938012] usb usb3-port6: couldn't allocate usb_device
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'

```

Removing/reinserting the two USB receivers doesn't add anything to dmesg output - guessing because of the "xHCI host controller not responding, assume dead" ?

---

### Post by misnoma on 2022-05-05
I also tried the following:

```
echo -n "0000:06:00.3" > /sys/bus/pci/drivers/xhci_hcd/unbind
echo -n "0000:06:00.3" > /sys/bus/pci/drivers/xhci_hcd/bind

dmesg | grep -v audit

[ 1964.982195] xhci_hcd 0000:06:00.3: remove, state 4
[ 1964.982204] usb usb4: USB disconnect, device number 1
[ 1964.982632] xhci_hcd 0000:06:00.3: USB bus 4 deregistered
[ 1964.982639] xhci_hcd 0000:06:00.3: remove, state 1
[ 1964.982641] usb usb3: USB disconnect, device number 1
[ 1964.983227] xhci_hcd 0000:06:00.3: USB bus 3 deregistered
[ 1968.894563] xhci_hcd 0000:06:00.3: xHCI Host Controller
[ 1968.894574] xhci_hcd 0000:06:00.3: new USB bus registered, assigned bus number 3
[ 1968.894740] xhci_hcd 0000:06:00.3: hcc params 0x0278ffe5 hci version 0x110 quirks 0x0000000000000410
[ 1968.895203] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[ 1968.895207] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1968.895209] usb usb3: Product: xHCI Host Controller
[ 1968.895210] usb usb3: Manufacturer: Linux 5.15.0-27-generic xhci-hcd
[ 1968.895212] usb usb3: SerialNumber: 0000:06:00.3
[ 1968.895392] hub 3-0:1.0: USB hub found
[ 1968.895407] hub 3-0:1.0: 6 ports detected
[ 1968.897676] xhci_hcd 0000:06:00.3: xHCI Host Controller
[ 1968.897680] xhci_hcd 0000:06:00.3: new USB bus registered, assigned bus number 4
[ 1968.897683] xhci_hcd 0000:06:00.3: Host supports USB 3.1 Enhanced SuperSpeed
[ 1968.897700] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
[ 1968.897723] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[ 1968.897725] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1968.897727] usb usb4: Product: xHCI Host Controller
[ 1968.897728] usb usb4: Manufacturer: Linux 5.15.0-27-generic xhci-hcd
[ 1968.897729] usb usb4: SerialNumber: 0000:06:00.3
[ 1968.897824] hub 4-0:1.0: USB hub found
[ 1968.897835] hub 4-0:1.0: 4 ports detected

```

So whilst it seems to reset the controller, it still doesn't find the plugged-in modules.

---

