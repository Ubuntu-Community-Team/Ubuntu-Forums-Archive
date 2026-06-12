---
title: "[SOLVED] Unable to detect the usb serial ti_usb_3410_5052 Ubuntu 8.1"
date: 2008-11-12
forum: Desktop Environments
---

### Post by techie_india on 2008-11-12
Hi all,

Im using ti_usb_3410_5052 ic.

I have also upgraded from ubuntu 8.04 to 8.1 ( thinking it might detect it )

When I plugin it , and when I do dmesg -c
it shows this :

```
[ 5781.424026] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 5781.617669] usb 4-1: configuration #1 chosen from 1 choice
[ 5781.621408] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[ 5781.621424] firmware: requesting ti_usb-3410.bin
[ 5781.666391] usb 4-1: ti_download_firmware - firmware not found
[ 5781.666684] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
```

I have added the 026_ti_usb_3410_5052.rules in the /etc/udev/rules.d directory which is given in the link : [http://www.openpages.info/huawei.html]("http://www.openpages.info/huawei.html")

Also when I do lsusb , it shows :

```
Bus 004 Device 008: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
```

Im not able to detect the IC :confused:

Please anybody help how to detect the IC . Its becoming very annoying :(

Thanks and Regards
Anshuman Srivastava

---

