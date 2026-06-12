---
title: "Externel Hard Drive issue, can`t figure this one out"
date: 2009-02-12
forum: General Help
---

### Post by nothingspecial on 2009-02-12
Rebooted my media server. Suddenly my drive`s not mounted. Doesn`t even show up in fdisk or lsusb.

Plug it in to my laptop and there it is.

Swap usb ports still not recognised.

Plug printer into both usb ports just tried and no problems.

So it`s not the drive - mounts fine on my laptop
It`s not the usb sockets - the printer works with both.

Anyone know what`s up?

---

### Post by perrti-y02 on 2009-02-12
Try opening the partition editor whilst it is plugged in. That sometimes works for me, but could do exactly the same thing as fdisk.

---

### Post by Neural oD on 2009-02-12
did u try sudo fdisk -l

---

### Post by nothingspecial on 2009-02-12
> **perrti-y02 said:**
> Try opening the partition editor whilst it is plugged in. That sometimes works for me, but could do exactly the same thing as fdisk.

Thanks for the reply - not there?!?

---

### Post by nothingspecial on 2009-02-12
> **Neural oD said:**
> did u try sudo fdisk -l

Yep - not there?!?

---

### Post by Neural oD on 2009-02-12
strange - maybe it has something to do with that usb port.
Some things require a certain level of power to be present in the usb port - others don't, so sometimes this can be quite difficult to problem solve!

---

### Post by perrti-y02 on 2009-02-12
That would tell you if it is found at all by the machine. Wouldn't help beyond that.

---

### Post by Neural oD on 2009-02-12
hence - maybe your printer will work on the port - but the disk might not. Has the external hard drive got a power cable - or is it getting the power from the usb

---

### Post by nothingspecial on 2009-02-12
This is what`s doing my head in. The laptop sees it. The printer works in both usb ports but it doesn`t.:confused:

---

### Post by Neural oD on 2009-02-12
you can type lsusb -v 
to get more detailed info on the usb devices

---

### Post by nothingspecial on 2009-02-12
The drive gets power from the wall socket. The verbose option still gives nothing.

---

### Post by Slim Odds on 2009-02-12
Watch the system log when you plug in the device. I will probably tell you what went wrong.

---

### Post by Neural oD on 2009-02-13
yes - have a look at what dmesg tells you - it should give some useful info
 - well hopefully anyway

---

### Post by nothingspecial on 2009-02-13
I`ll have a go when I get home in about an hour.

Thanks

---

### Post by nothingspecial on 2009-02-13
I guess this is the relevant info from dmesg
```

usb 5-5: new high speed USB device using ehci_hcd and address 8
[56029.138323] end_request: I/O error, dev fd0, sector 0
[56029.162274] end_request: I/O error, dev fd0, sector 0
[78883.780633] usblp0: removed
```

Any ideas?

---

### Post by nothingspecial on 2009-02-13
> **nothingspecial said:**
> I guess this is the relevant info from dmesg
```

usb 5-5: new high speed USB device using ehci_hcd and address 8
[56029.138323] end_request: I/O error, dev fd0, sector 0
[56029.162274] end_request: I/O error, dev fd0, sector 0
[78883.780633] usblp0: removed
```

Any ideas?

Although it turns out that dev fd0 is a floppy drive. Just did it again and dmesg returns
```

usb 5-5: new high speed USB device using ehci_hcd and address 10
[147463.605239] usb 5-5: new high speed USB device using ehci_hcd and address 13
[148118.830861] usb 5-5: new high speed USB device using ehci_hcd and address 14
[148119.130316] usb 5-5: new high speed USB device using ehci_hcd and address 15
```
So it doesn`t seem to be giving any errors other than it keeps using diferent numbered adresses - I don`t know if that`s relevant.

So here`s sudo fdisk -l```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6edfd38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c937cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512   83  Linux
```

/dev/sdb is my back up drive plugged in since this problem.

---

### Post by nothingspecial on 2009-02-18
Well, I rebooted today and there it is, no data loss no nothing, working perfectly.

This one`s got me stumped.

---

