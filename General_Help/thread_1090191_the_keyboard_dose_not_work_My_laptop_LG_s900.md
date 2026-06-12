---
title: "the keyboard dose not work My laptop LG s900"
date: 2009-03-08
forum: General Help
---

### Post by ahmedks on 2009-03-08
good morning


I have laptop LG s900 .I install  Ubuntu 8.10  Linux 2.6.27-13-generic .... .... every things is good but the keyboard dose not work. 

 dmesg :

[    5.158009] input: HID Keyboard Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input2
[    5.158143] input,hidraw0: USB HID v1.10 Keyboard [HID Keyboard Device] on usb-0000:00:1a.0-2
[    5.178923] input: HID Keyboard Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.1/input/input3
[    5.179134] input,hidraw1: USB HID v1.10 Device [HID Keyboard Device] on usb-0000:00:1a.0-2





Thanks

---

### Post by Sonema on 2009-07-12
> **ahmedks said:**
> good morning


I have laptop LG s900 .I install  Ubuntu 8.10  Linux 2.6.27-13-generic .... .... every things is good but the keyboard dose not work. 

 dmesg :

[    5.158009] input: HID Keyboard Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input2
[    5.158143] input,hidraw0: USB HID v1.10 Keyboard [HID Keyboard Device] on usb-0000:00:1a.0-2
[    5.178923] input: HID Keyboard Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.1/input/input3
[    5.179134] input,hidraw1: USB HID v1.10 Device [HID Keyboard Device] on usb-0000:00:1a.0-2





Thanks i have same laptop and i solved it like this:
You need write 
i8042.nopnp=1 i8042.dumbkbd=1 
on /boot/grub/menu.lst

---

