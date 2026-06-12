---
title: "no webcam showing in lsusb"
date: 2009-05-01
forum: General Help
---

### Post by donal on 2009-05-01
Hi,
i did have my webcam working at one point on my DELL XPS M1330 laptop.
this has an inbuilt webcam. now i get nothing.

i see no flashing lights when i boot up and lsusb shows this (no mention of a webcam):

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


does this sound like a hardware problem to you guys?

i took a look in the bios but could not see anything related to a webcam. should the bios show some sort of webcam device in there?

just want to confirm if this is something i can tinker with and research a bit to get it to work in ubuntu of if the thing is just broken and i need a new webcam...i don't dual boot windows so i can't check if it works in there or not.

i also tried dmesg | grep -i webcam and got nothing back either...

would appreciate any help i have been googling and fiddling with this for the last few hours and am just about to give up hope on it...

thanks
Dónal

---

### Post by geraldm on 2009-05-01
Hi,
The webcam would only show up in lsusb if it were a usb device.  There is a possibility that it is not.  If the device is detected, there would be some information in the boot logs or dmesg.  You might also try
sudo lshw

regards
Gerald

---

### Post by donal on 2009-05-02
thx for the reply Gerald. I went through sudo lshw too and found nothing there either. output file is attached.  i stepped through the dmesg logs too but could not find anything with a webcam in it.

also i see no lights flashing on this at the bootup stage...which i am pretty sure used to happen before...starting to suspect the camera itself is broken or someway got disconnected.

open to any other suggestions...this laptop is out of its dell warrany now so i am reluctant to contact them to fix it.

anybody know if the bios should show some entry for a webcam?


thanks
Dónal

---

