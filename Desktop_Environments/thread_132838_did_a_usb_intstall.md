---
title: "did a usb intstall"
date: 2006-02-19
forum: Desktop Environments
---

### Post by arg on 2006-02-19
after doing a install via a usb thumb drive now when i put a usb thumb drive in i get an error

Warning: device /dev/sda1 is already handled by /etc/fstab, supplied label is ignored
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

anyone know how to fix this?

thanks heaps
alan.

---

### Post by xmastree on 2006-02-19
Well... Assuming the USB drive isn't essential to the system (i.e. it boots without it) I would take a look at your /etc/fstab and comment out the line containing /dev/sda1 since it probably doesn't need to be in there any more.

---

