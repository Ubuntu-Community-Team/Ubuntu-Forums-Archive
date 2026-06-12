---
title: "How to mount USB devices"
date: 2006-01-10
forum: Desktop Environments
---

### Post by endangst on 2006-01-10
I've read that some people can mount their USB card reader and others can't.

Here is the last few lines of dmesg (after plugging in my hub which my card reader is plugged into) and the lsusb:

```

[4294880.948000] usb 2-1: new full speed USB device using ohci_hcd and address 6[4294881.057000] hub 2-1:1.0: USB hub found
[4294881.059000] hub 2-1:1.0: 4 ports detected
[4294881.298000] usb 2-1.2: new full speed USB device using ohci_hcd and address 7
endangst@ubuntu:~$ lsusb
Bus 002 Device 007: ID 0d8c:5000 C-Media Electronics, Inc.
Bus 002 Device 006: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 001: ID 0000:0000
endangst@ubuntu:~$ pmount /dev/sda1
Error: could not determine real path of the device: No such file or directory
endangst@ubuntu:~$

```

Any help is greatly appreciated! :)

---

### Post by soulestream on 2006-01-10
you might want to plug in your card reader, then 

plug in your memory card.

then give us a dmesg


soule

---

### Post by endangst on 2006-01-11
Nothing new shows up in dmesg after plugging in the memory card.  The light on the card reader doesn't light up either when the memory card is inserted.

---

### Post by youyoud on 2007-10-26
i have the same problems with my sdcard
lsusb 
Bus 002 Device 006: ID 0d8c:5000 C-Media Electronics, Inc. 

mount: périphérique spécial /dev/sdb1 n'existe pas


sudo mount /dev/sdb1 /media/cartesd
mount: /dev/sdb1 n'est pas un périphérique valide de type bloc

---

