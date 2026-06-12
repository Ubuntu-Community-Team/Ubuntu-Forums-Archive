---
title: "3 minute boot delay in 9.04. Suspect USB device problem."
date: 2009-04-25
forum: General Help
---

### Post by Beastie Boy on 2009-04-25
I have just done a fresh install of 9.04 on my Acer Aspire 9110 series laptop. The boot process pauses at around 11 seconds, and this seems to be the point at which the Bluetooth device is switched on. The Bluetooth is controlled by a button along with the wireless network device. I usually leave Bluetooth off, but 9.04 insist on switching it on for some reason.
I never had this problem with previous versions.

Here is the dmesg output from the period when the delay occurs:

[ 11.110893] EIP: [<f7fa52c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ES
P 0068:f619bc54
[ 11.110906] ---[ end trace 9bd66193deb28a9c ]---
[ 11.500080] Clocksource tsc unstable (delta = -341257333 ns)
[ 11.588074] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 11.759586] usb 4-2: configuration #1 chosen from 1 choice
[ 11.790916] Bluetooth: Generic Bluetooth USB driver ver 0.3
[ 11.791032] usbcore: registered new interface driver btusb
[ 189.996709] lp: driver loaded but no devices found
[ 190.062114] Adding 506008k swap on /dev/sda5. Priority:-1 extents:1 across:5
06008k


Any help would be appreciated as one of my main reasons for upgrading to 9.04 was quicker boot.
I don't use Bluetooth and would be happy if the device wasn't loaded. I have looked to see if it can be disabled in the BIOS, but there is no option for it.

Is it possible to prevent the boot process from turning on device 'usb 4-2'? Or is it possible to reduce the time spent searching for devices?

Many thanks, Beastie.

---

