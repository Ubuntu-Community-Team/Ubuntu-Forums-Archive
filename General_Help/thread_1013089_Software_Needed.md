---
title: "Software Needed"
date: 2008-12-16
forum: General Help
---

### Post by interse on 2008-12-16
Is there a program which will make an   .iso     image bootable from a USB memory stick?   What is the name(s)?      Thanks

---

### Post by adult swim on 2008-12-16
sudo apt-get install usb-creator
it should show up in system>administration>Create a usb startup disk

if you are running 8.10 its already there

---

### Post by interse on 2008-12-16
I am using 8.04.  The command   apt-get install usb-creator   responds by indicating that the usb-creator is NOT available.   In which repository is it located?

---

### Post by cariboo on 2008-12-16
Have you tried dd, it is installed by default use it like this:

```
sudo dd if=file.iso of=/dev/sdb
```

where file.iso= your iso image and /dev/sdb= your usb device.

The above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

### Post by Yardarm on 2008-12-16
UNetbootin is another option that for sure works in 8.04.  There's a HOWTO here:

[http://tombuntu.com/index.php/2008/08/27/create-a-bootable-usb-drive-or-memory-card/]("http://tombuntu.com/index.php/2008/08/27/create-a-bootable-usb-drive-or-memory-card/")

---

