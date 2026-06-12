---
title: "Bluetooth keyboard and mouse disconnects"
date: 2009-03-05
forum: Desktop Environments
---

### Post by sullenx on 2009-03-05
Hello, 

   I am using a microsoft keyboard and mouse through a USB Bluetooth dongle it came with in Ubuntu 8.10.  In 8.04, i was okay with this setup since i had both the hcitool, hciconfig and hidd tools.  Now, in 8.10, the hidd tool has been removed and i find it painful to setup bluetooth devices through the bluetooth-wizard.

This is my problem: I can successfully pair my keyboard and mouse using the bluetooth-wizard.  To solve the disconnect problem, i set my usb bluetooth dongle to do page scan: 

sudo hciconfig hci0 pscan

Everything works well, until somehow usbfs comes in and my keyboard and mouse get unpaired.  I try rebooting and nothing!

Any help would be appreciated!

---

