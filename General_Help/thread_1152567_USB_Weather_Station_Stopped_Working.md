---
title: "USB Weather Station Stopped Working"
date: 2009-05-07
forum: General Help
---

### Post by Ando140 on 2009-05-07
I recently upgraded my Ubuntu server to 8.04 and now my weather station no longer works.  The weather station is a Thermor BIOS weather station.  It seemed to work fine before the upgrade, but now it doesn't show up in /dev
I did some research and tried the fix for the ehci_hcd issue (this bug [https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/88746](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/88746) ), but it doesn't seem to be fixing my problem.
Here's the dmesg output:
> 
[  982.634867] ehci_hcd 0000:00:0b.2: USB bus 5 deregistered
[  982.635013] ACPI: PCI interrupt for device 0000:00:0b.2 disabled
[ 1052.251889] usb 3-3: new full speed USB device using ohci_hcd and address 14
[ 1052.469897] usb 3-3: device descriptor read/all, error -84
[ 1052.651871] usb 3-3: new full speed USB device using ohci_hcd and address 15
[ 1052.869859] usb 3-3: device descriptor read/all, error -84
[ 1053.051859] usb 3-3: new full speed USB device using ohci_hcd and address 16
[ 1053.089854] usb 3-3: device descriptor read/8, error -84
[ 1053.219836] usb 3-3: device descriptor read/8, error -84
[ 1053.501886] usb 3-3: new full speed USB device using ohci_hcd and address 17
[ 1053.539815] usb 3-3: device descriptor read/8, error -84
[ 1053.669805] usb 3-3: device descriptor read/8, error -84
[ 1300.891642] usb 3-3: new full speed USB device using ohci_hcd and address 18
[ 1301.109614] usb 3-3: device descriptor read/all, error -84
[ 1301.291594] usb 3-3: new full speed USB device using ohci_hcd and address 19
[ 1301.509595] usb 3-3: device descriptor read/all, error -84
[ 1301.691579] usb 3-3: new full speed USB device using ohci_hcd and address 20
[ 1301.729570] usb 3-3: device descriptor read/8, error -84
[ 1301.859561] usb 3-3: device descriptor read/8, error -84
[ 1302.141563] usb 3-3: new full speed USB device using ohci_hcd and address 21
[ 1302.179540] usb 3-3: device descriptor read/8, error -84
[ 1302.309531] usb 3-3: device descriptor read/8, error -84

Also, this message appears in /var/log/messages when I connect the usb weather station
> 
kernel: [  629.479359] usb 3-3: new full speed USB device using ohci_hcd and address 6
kernel: [  629.879339] usb 3-3: new full speed USB device using ohci_hcd and address 7
kernel: [  630.279331] usb 3-3: new full speed USB device using ohci_hcd and address 8
kernel: [  630.729340] usb 3-3: new full speed USB device using ohci_hcd and address 9
kernel: [  637.199049] usb 3-3: new full speed USB device using ohci_hcd and address 10
kernel: [  637.609019] usb 3-3: new full speed USB device using ohci_hcd and address 11
kernel: [  638.009016] usb 3-3: new full speed USB device using ohci_hcd and address 12
kernel: [  638.458994] usb 3-3: new full speed USB device using ohci_hcd and address 13

Anyone have any idea what might be causing the problem and how I could fix it?

Thanks,
Andy

---

### Post by Ando140 on 2009-05-08
I should also mention I upgraded from 6.06.1 Dapper Drake.

Thanks for any help,
Andy

---

