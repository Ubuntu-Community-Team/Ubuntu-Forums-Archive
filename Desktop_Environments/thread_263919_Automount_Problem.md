---
title: "Automount Problem"
date: 2006-09-23
forum: Desktop Environments
---

### Post by at_a_loss on 2006-09-23
Hi Everyone,

I just bought a new 2GB usb flash drive today, and I'm having automount issues with it.  The problem is this -- upon reboot, the first time I plug it in, it automounts fine.  Then I remove it (by right clicking on the desktop icon and selecting "eject").  The light goes off on the drive, and I remove it.  When I plug it back in, it won't automount!  I can manually mount it with no problems.  If I reboot, it automounts fine.

I have another flash drive (256 MB) that doesn't have this problem.  Is it an issue with they type of drive I've purchased (Simpletech USB 2.0 2GB Flash Drive)?

I'm running Dapper, kernel version 2.6.15-27-386, on an averatec 3715 laptop.  Here's my /var/log/messages from when I plug it in once, remove it, and plug it in again.  Any help will be sincerely appreciated!


```
Sep 23 21:59:28 localhost kernel: [17179664.496000] usb 4-2: new high speed USB device using ehci_hcd and address 2
Sep 23 21:59:28 localhost kernel: [17179664.836000] Initializing USB Mass Storage driver...
Sep 23 21:59:28 localhost kernel: [17179664.836000] scsi0 : SCSI emulation for USB Mass Storage devices
Sep 23 21:59:28 localhost kernel: [17179664.836000] usbcore: registered new driver usb-storage
Sep 23 21:59:28 localhost kernel: [17179664.836000] USB Mass Storage support registered.
Sep 23 21:59:33 localhost kernel: [17179669.836000]   Vendor: Simple    Model: Flash Disk 2.0    Rev: 2.00
Sep 23 21:59:33 localhost kernel: [17179669.836000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Sep 23 21:59:33 localhost kernel: [17179669.912000] Driver 'sd' needs updating - please use bus_type methods
Sep 23 21:59:38 localhost kernel: [17179675.008000] ready
Sep 23 21:59:38 localhost kernel: [17179675.008000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
Sep 23 21:59:39 localhost kernel: [17179675.008000] sda: Write Protect is off
Sep 23 21:59:39 localhost kernel: [17179675.012000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
Sep 23 21:59:39 localhost kernel: [17179675.016000] sda: Write Protect is off
Sep 23 21:59:39 localhost kernel: [17179675.016000]  sda: sda1
Sep 23 21:59:39 localhost kernel: [17179675.016000] sd 0:0:0:0: Attached scsi removable disk sda
Sep 23 21:59:39 localhost kernel: [17179675.036000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 23 22:01:02 localhost kernel: [17179758.252000] usb 4-2: USB disconnect, address 2
Sep 23 22:01:10 localhost kernel: [17179766.556000] usb 4-2: new high speed USB device using ehci_hcd and address 3
Sep 23 22:01:10 localhost kernel: [17179766.700000] scsi1 : SCSI emulation for USB Mass Storage devices
Sep 23 22:01:15 localhost kernel: [17179771.700000]   Vendor: Simple    Model: Flash Disk 2.0    Rev: 2.00
Sep 23 22:01:15 localhost kernel: [17179771.700000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Sep 23 22:01:20 localhost kernel: [17179776.796000] ready
Sep 23 22:01:20 localhost kernel: [17179776.796000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
Sep 23 22:01:20 localhost kernel: [17179776.796000] sda: Write Protect is off
Sep 23 22:01:20 localhost kernel: [17179776.800000] SCSI device sda: 4077568 512-byte hdwr sectors (2088 MB)
Sep 23 22:01:20 localhost kernel: [17179776.804000] sda: Write Protect is off
Sep 23 22:01:20 localhost kernel: [17179776.804000]  sda: sda1
Sep 23 22:01:20 localhost kernel: [17179776.804000] sd 1:0:0:0: Attached scsi removable disk sda
Sep 23 22:01:20 localhost kernel: [17179776.804000] sd 1:0:0:0: Attached scsi generic sg0 type 0
```

---

### Post by at_a_loss on 2006-09-23
OK, after hunting around on the forums, I found this post:

[http://www.ubuntuforums.org/showthread.php?t=196700]("http://www.ubuntuforums.org/showthread.php?t=196700")

Apparently some usb flash drives only automount if the sd_mod module is not already loaded.  Indeed, this is exactly what happens with mine.  If I remove the drive and type "sudo modprobe -r sd_mod", the drive will automount when I plug it back in.

There was no resolution in this post -- anyone have any suggestions?

---

### Post by at_a_loss on 2006-09-24
Still no luck!  Can someone please answer the following questions:

1) Is there some way I can force the module sd_mod to be unloaded when I remove the USB device?  Is there a script that is run when it is unloaded?

2) Can I put something in my fstab so that when I manually mount it, an icon appears on my desktop and I have permission to read and write to it?  Right now, when I mount it via "sudo mount /dev/sda1 /mnt/usb/" only root has permission to write.


Thanks in advance!  This is a real bummer....

---

### Post by at_a_loss on 2006-09-25
bump!

I managed to modify my fstab so that I can mount the device with read/write permissions as a user.

Still looking for a solution to the overall problem -- is this an ubuntu bug?  Should I report it or something?  If so, how?

---

### Post by TrinitronX on 2006-09-30
There may be a way to do this with a script on drive removal using udev.
My attempts at using udev to run a backup script on plugging in my drive have failed for some reason, but perhaps doing something not involving file IO to the drive on removal would work in a script.
check out this guide on udev: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by David Corrales on 2006-10-29
> **at_a_loss said:**
> OK, after hunting around on the forums, I found this post:

[http://www.ubuntuforums.org/showthread.php?t=196700]("http://www.ubuntuforums.org/showthread.php?t=196700")

Apparently some usb flash drives only automount if the sd_mod module is not already loaded.  Indeed, this is exactly what happens with mine.  If I remove the drive and type "sudo modprobe -r sd_mod", the drive will automount when I plug it back in.

There was no resolution in this post -- anyone have any suggestions?

Exact same problem here :(

---

