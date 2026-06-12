---
title: "Sansa Fuze refuses to be detected by Arch Linux"
date: 2009-03-14
forum: General Help
---

### Post by Grant A. on 2009-03-14
Hello, I use Arch Linux i686, and when I try to plug in my 4GB Sansa Fuze, it fails to be detected by Linux as a USB mass storage device, even when in MSC mode. Does anyone know how to fix this problem?

Here is my dmesg | tail output:

```

usb 3-1: device descriptor read/64, error -71
usb 3-1: device descriptor read/64, error -71
usb 3-1: new full speed USB device using uhci_hcd and address 19
usb 3-1: device descriptor read/64, error -71
usb 3-1: device descriptor read/64, error -71
usb 3-1: new full speed USB device using uhci_hcd and address 20
usb 3-1: device not accepting address 20, error -71
usb 3-1: new full speed USB device using uhci_hcd and address 21
usb 3-1: device not accepting address 21, error -71
hub 3-0:1.0: unable to enumerate USB device on port 1

```

Does anyone know how I may remedy this problem?


**Specs:**

Arch Linux i686
Intel Centrino Processor
4 USB 2.0 ports
4GB Sansa Fuze v.02.01.09
Linux Kernel 2.6.28.7 (Stock, Vanilla)

---

### Post by Grant A. on 2009-03-15
Any ideas as to how to rectify this?

---

### Post by SuperSonic4 on 2009-03-15
What happens if you do ```
sudo fdisk -l
```? That will see if the device is recognised.

---

### Post by Grant A. on 2009-03-15
```

Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c2404

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3039    24410736   83  Linux
/dev/sda2            3040        6078    24410767+  83  Linux
/dev/sda3            6079        6406     2634660   82  Linux swap / Solaris
/dev/sda4            6407        9705    26499217+  83  Linux

```

sda1 is my root partition
sda2 is my home partition
sda3 is my swap partition
sda4 is my files partition

I don't see anything that might be my Fuze in there though, how can I fix this?

---

### Post by kk0sse54 on 2009-03-15
How about asking this over on the Arch forum, you'd get a lot more specific help there.

Edit: sweet I see you got a thread going on there too :)

---

### Post by Grant A. on 2009-03-15
> **C!oud said:**
> How about asking this over on the Arch forum, you'd get a lot more specific help there.

Edit: sweet I see you got a thread going on there too :)

Yeah, but no one has replied. :(

---

### Post by miegiel on 2009-03-15
Try forcing USB 1.1, try a different USB cable and try the disk in another machine.

---

### Post by chris200x9 on 2010-01-09
bump exact same problem ```
rmmod ehci-hcd 
``` did not help?

---

