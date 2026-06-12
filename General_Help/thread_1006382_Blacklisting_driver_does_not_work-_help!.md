---
title: "Blacklisting driver does not work- help!"
date: 2008-12-09
forum: General Help
---

### Post by 77bridge on 2008-12-09
Hi *,

The documented procedures for blacklisting this particular driver doesn't seem to work- I'm totally at a dead end.  I'm trying to blacklist the 'usb_storage' (or usb-storage) module so that it does not start up when I plug in my iPod (b/c I want VMware drivers to access it).

I've tried the approach described here: [HOWTO: Prevent (blacklist) modules from loading]("http://ubuntuforums.org/showthread.php?t=166624") but that hasn't worked. (ubuntuforums.org/showthread.php?t=166624)

For example, when I restart the machine and I execute: 'lsmod | grep usb' I get the following output:
usbhid 32128 0
hid 38784 1 usbhid
usbcore 146412 5 uvcvideo,usbhid,ehci_hcd,uhci_hcd

That's ok. Now when I plug in my iPod, I execute the same command and I get the following output:
usb_storage 73664 0
libusual 19108 1 usb_storage
usbhid 32128 0
hid 38784 1 usbhid
scsi_mod 151436 6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata
usbcore 146412 7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci _hcd

usb_storage is the very first module listed, yet my /etc/modprobe.d/blacklist and /etc/modprobe.d/blacklist-custom files both have the following lines:
blacklist usb-storage
blacklist usb_storage

So that's my question: any idea how I can actually blacklist usb_storage so that it doesn't start up when I plug in my iPod?

Thanks!!! :)

---

### Post by caljohnsmith on 2008-12-09
You could "brute force" blacklist the usb-storage module to make sure it doesn't get loaded by simply changing the name of the original kernel module:
```
cd /lib/modules/`uname -r`/kernel/drivers/usb/storage
sudo mv usb-storage.ko usb-storage.ko.backup
```
How about giving that shot and let me know if it works.

---

### Post by 77bridge on 2008-12-10
Thanks!  That did indeed supress the driver from loading!  :)

Unfortunately, now my virtual machine is not able to recognize the iPod.  I'm going to play around with the drivers on the guest, but I suspect there might be some dependency on the hosts drivers.  I'm close to giving up on this thing...

---

### Post by CyborgMax on 2009-02-24
Hi there. This does not work for me. Even when I rename the whole folder storage to backup-storage. What can I do? Using ubuntu-desktop 8.04.2 x64.

---

