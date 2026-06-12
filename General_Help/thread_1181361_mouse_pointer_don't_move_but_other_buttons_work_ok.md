---
title: "mouse pointer don't move but other buttons work ok"
date: 2009-06-07
forum: General Help
---

### Post by sotoskawasaki on 2009-06-07
Hi. I have a sweex usb laser mouse, which when I plug in my laptop, doesn't move the pointer however I move the mouse. The strange thing is that all the other buttons work great!! With lsusb I get:

> sotos@kawasaki:~$ lsusb
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04d9:1166 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sotos@kawasaki:~$ 
 

The mouse is the forth line.

I checked on xorg.conf and it doesn't have a section for input device like the xorg.conf file of earlier ubuntu versions had. I am using 9.04

---

