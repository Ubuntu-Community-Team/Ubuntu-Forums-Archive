---
title: "[SOLVED] Unable to detect the usb serial ti_usb_3410_5052"
date: 2008-11-12
forum: Desktop Environments
---

### Post by techie_india on 2008-11-12
Hi all ,
This is same problem which I m facing in the ubuntu 8.04.

I have upgraded the ubuntu 8.04 to 8.1.

When I plug in the ti_usb_3410_5052 ic ( also I have added the rules given in the site ---> [http://www.openpages.info/huawei.html]("http://www.openpages.info/huawei.html")

It gives the following error:

```
[ 3555.248056] usb 4-2: USB disconnect, address 5
[ 3677.040028] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 3677.289673] usb 4-1: configuration #1 chosen from 1 choice
[ 3677.293415] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[ 3677.293429] firmware: requesting ti_usb-3410.bin
[ 3677.297538] usb 4-1: ti_download_firmware - firmware not found
[ 3677.297561] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
[ 3986.272306] usb 4-1: USB disconnect, address 6
```

when I have done lsusb , it shows :
```
Bus 004 Device 007: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
```

Also a new error which was not there in Ubuntu 8.04:
```
[ 3677.293429] firmware: requesting ti_usb-3410.bin
[ 3677.297538] usb 4-1: ti_download_firmware - firmware not found
```

Im not able to get the solution how to detect the IC.

Please Can anybody help me on this issue as it is very urgent 


Thanks and reagrds
Anshuman Srivastava

---

### Post by rynoprinsloo on 2008-11-14
Hi techie_india, 

> [ 3677.293429] firmware: requesting ti_usb-3410.bin
[ 3677.297538] usb 4-1: ti_download_firmware - firmware not found

This is because of the firmware lying on the wrong place, but the following will do the trick. I found it at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/236247]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/236247") in my quest to get it working myself.

```
sudo cp /lib/firmware/$(uname -r)/ti_3410.fw /lib/firmware/ti_usb-3410.bin
```

This will resolve the firmware issue. Please post your results.

I've fixed it for 8.04 last night and will post a how to as soon as I get time.

Ryno

---

### Post by techie_india on 2008-11-15
Hi rynoprinsloo ,

Thanks a lot .
It had solved my problem

Thanks and Regards
Anshuman Srivastava

---

