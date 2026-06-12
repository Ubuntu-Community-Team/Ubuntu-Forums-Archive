---
title: "USB device mounting"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Nachtengel on 2005-12-16
I'm trying to mount an iPod Shuffle in order to format it, however I am having some difficulty finding which device address I should be using.

Nominally I would have thought plugging it into a usb port would have had it addressed as /dev/usb0 or /dev/usb1 or the like.  But these addresses apprently are not there.  So I took a look at my /dev/ directory, and found /dev/hdc, which is a good canidate, since I only have two hard drives (hda and hdb respectively).  However, trying to mount it, I get the error: 

user@host>$ mount -t msdos /dev/hdc /home/user/iPod
mount: no medium found

which may or may not be totally truthful, since the iPod Shuffle I'm trying to mount for formatting purposes has been flaking out recently (and hence my need to format it).  

Does anyone have any suggestions as to if I'm trying to mount the correct device?  Do usb devices normally appear at /dev/usb#?

---

### Post by fog on 2005-12-16
try use /dev/sda1 not /dev/hdc

---

### Post by Nachtengel on 2005-12-16
Thanks for the advice, however it does not appear that I have a /dev/sda1 device.. in fact there is nothing in the location /dev/sd*.  This may be a function of the device being somewhat broken.  But I don't really know if it is or not.  Any further suggestions?

Also for clarification, all usb devices will be located at /dev/sda# (where # is the port #)?

---

### Post by fog on 2005-12-16
No, sda is the first usb disk.
/dev/sda1: the first partition in that disk.
sdb is the second disk 
/dev/sdb5 is the 5th partition in the second disk, etc.

---

