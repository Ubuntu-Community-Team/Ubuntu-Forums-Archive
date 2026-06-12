---
title: "Wakeup from Standby S3 with Remote doesnt work"
date: 2009-01-11
forum: General Help
---

### Post by stronzo on 2009-01-11
Hi!
I want to wake up my xubuntu with my remote. its receiver is connected via usb. i got a wakeup working with the remote, but only once and never again. what have i done:
*activated power on via usb (S3) in the BIOS
*when the machine is in suspend mode, the receiver of the remote is still on (led light on), that means it has power
*edited /etc/default/acpi-support , tried to add usbcore module to the whitelist, but doesnt work
*i catted /proc/acpi/wakeup
everything there is disabled

USB0 S3 disabled pci:0000:00:13.0
USB2 S3 disabled pci:0000:00:13.1

if i now go to suspend, the machine will not react on my remote.


if i activate one or both usbports that it looks like this

USB2 S3 enabled pci:0000:00:13.1

and the go to suspend the machine immediately wakes up again.
it seems that my remotereceiver is sending continously signals to the usb port..

has anyone an idea how i can get this to work, or even the same problems?
thanks for answers!

---

### Post by stronzo on 2009-01-11
push

---

### Post by stronzo on 2009-01-15
push

---

### Post by stronzo on 2009-01-20
push.....

---

### Post by stronzo on 2009-01-23
still no solution in sight, plz help

---

### Post by stronzo on 2009-02-11
just another push

---

### Post by stronzo on 2009-03-28
another push

---

