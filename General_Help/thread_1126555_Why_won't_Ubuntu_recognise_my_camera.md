---
title: "Why won't Ubuntu recognise my camera?"
date: 2009-04-12
forum: General Help
---

### Post by jcorden on 2009-04-12
Have just upgraded to version 8.

When I try to import photos from my camera connected via USB using F-Spot or gThumb I get the following error message.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

The same error happens with two types of camera. I did not have this problem with version 7.

Help appreciated.

---

### Post by jcorden on 2009-04-12
Have just upgraded to version 8.

When I try to import photos from my camera connected via USB using F-Spot or gThumb I get the following error message.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

The same error happens with two types of camera. I did not have this problem with version 7.

Help appreciated.

---

### Post by jcorden on 2009-04-13
Have just upgraded to version 8.

When I try to import photos from my camera connected via USB using F-Spot or gThumb I get the following error message.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

The same error happens with two types of camera. I did not have this problem with version 7.

Help appreciated.

---

### Post by jcorden on 2009-04-15
I have just upgraded from v7 to v8.04.2. There is a problem recognising my Canon Powershot A710 connected via USB cable. I have tried all the usual fixes suggested for this problem such as upgrading gphoto but had no success. This problem did not occur with version 7

gthumb gives the following error:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

F-Spot gives the following error:

Could not claim the usb device while connecting to the camera

Picasa just crashes when I try to import

I am sure this is a mounting/USB problem

lsusb gives the following:

Bus 002 Device 002: ID 091e:0003 Garmin International GPSmap (various models)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 014: ID 04a9:3138 Canon, Inc. PowerShot A710 IS
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 001: ID 0000:0000 

Would really appreciate some help, have posted 3 times now with no takers.

Thanks

---

### Post by Elfy on 2009-04-15
Threads merged - please odn;t post multiple threads on same issue. Give people time to answer.

---

### Post by quazi on 2009-04-15
It sounds like you might not be in the right group for camera access.  Check to see if you need to be a member of a certain group.

---

### Post by bsmith1051 on 2009-04-15
By upgrade you mean Ubuntu, right?  If so then you might now be having the infamous USB compatibility problem.  Try checking this log,
```
> dmesg | grep usb
```
and look for any error messages.

Until there's a proper fix (9.04?) the only workaround is to install an add-in USB card, and hope that it's one that is compatible.

---

### Post by jcorden on 2009-04-15
Gives the following - what does this mean?

Is the USB compatibility issue a new problem as it was fine in version 7

41.724790] usbcore: registered new interface driver usbfs
[   41.724813] usbcore: registered new interface driver hub
[   41.724829] usbcore: registered new device driver usb
[   41.726158] usb usb1: configuration #1 chosen from 1 choice
[   41.904895] usb usb2: configuration #1 chosen from 1 choice
[   42.074500] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   42.219439] usb 1-2: configuration #1 chosen from 1 choice
[   42.701412] usb 1-8: new high speed USB device using ehci_hcd and address 4
[   42.850857] usb 1-8: configuration #1 chosen from 1 choice
[   43.152639] usb 2-5: new full speed USB device using ohci_hcd and address 2
[   43.355431] usb 2-5: configuration #1 chosen from 1 choice
[   43.358528] usbcore: registered new interface driver libusual
[   43.361513] usb-storage: device found at 2
[   43.361514] usb-storage: waiting for device to settle before scanning
[   43.361567] usb-storage: device found at 4
[   43.361568] usb-storage: waiting for device to settle before scanning
[   43.361578] usbcore: registered new interface driver usb-storage
[   48.351835] usb-storage: device scan complete
[   48.353063] usb-storage: device scan complete
[  483.152000] usb 1-6: new high speed USB device using ehci_hcd and address 5
[  483.304000] usb 1-6: configuration #1 chosen from 1 choice
[  575.616000] usb 1-6: USB disconnect, address 5
[  628.876000] usb 1-6: new high speed USB device using ehci_hcd and address 6
[  629.028000] usb 1-6: configuration #1 chosen from 1 choice
[  718.168000] usb 1-6: USB disconnect, address 6
[  789.504000] usb 1-6: new high speed USB device using ehci_hcd and address 7
[  789.656000] usb 1-6: configuration #1 chosen from 1 choice
[ 1089.388000] usb 1-6: USB disconnect, address 7
[ 5611.640000] usb 1-6: new high speed USB device using ehci_hcd and address 8
[ 5611.792000] usb 1-6: configuration #1 chosen from 1 choice
[ 5911.428000] usb 1-6: USB disconnect, address 8
[ 6095.600000] usb 1-6: new high speed USB device using ehci_hcd and address 9
[ 6095.752000] usb 1-6: configuration #1 chosen from 1 choice
[ 6373.068000] usb 1-6: USB disconnect, address 9
[ 6376.988000] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 6377.140000] usb 1-6: configuration #1 chosen from 1 choice
[ 6676.780000] usb 1-6: USB disconnect, address 10
[ 7564.964000] usb 1-6: new high speed USB device using ehci_hcd and address 11
[ 7565.116000] usb 1-6: configuration #1 chosen from 1 choice
[ 7864.752000] usb 1-6: USB disconnect, address 11
[ 8045.428000] usb 1-6: new high speed USB device using ehci_hcd and address 12
[ 8045.580000] usb 1-6: configuration #1 chosen from 1 choice
[ 8345.220000] usb 1-6: USB disconnect, address 12
[ 8653.096000] usb 1-6: new high speed USB device using ehci_hcd and address 13
[ 8653.248000] usb 1-6: configuration #1 chosen from 1 choice
[ 8952.884000] usb 1-6: USB disconnect, address 13
[ 9222.512000] usb 1-6: new high speed USB device using ehci_hcd and address 14
[ 9222.664000] usb 1-6: configuration #1 chosen from 1 choice
[ 9522.300000] usb 1-6: USB disconnect, address 14

---

### Post by bsmith1051 on 2009-04-16
your DMESG log looks fine, I don't see any errors.  I assume that you tried/failed to use the camera since your last reboot, i.e., any errors would have been on this log?

also, yes, this USB problem is relatively new.  Some people reported 'it' back on v7 but a LOT of people have reported in v8.04 and 8.10.

---

### Post by jcorden on 2009-04-16
Yes - it is Ubuntu that I have upgraded.

Any ideas what I should try next if the USB connection appears to be ok?

---

### Post by jcorden on 2009-04-17
bump

---

### Post by hesperus on 2009-04-29
> **jcorden said:**
> bump
Have you tried to install gtkam? That could work. It looks as if your camera is detected correctly but if it is in PTP mode it won't mount. You need something like gtkam to connect in this case. 

Alternativly, there might be an option on your camera to switch to a usb mass storage device mode which will mount.

---

