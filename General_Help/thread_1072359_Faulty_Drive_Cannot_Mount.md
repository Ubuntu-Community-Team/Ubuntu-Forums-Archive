---
title: "Faulty Drive: Cannot Mount"
date: 2009-02-17
forum: General Help
---

### Post by kneewax on 2009-02-17
OK, so I may be on a loser here regardless.  Since my laptop went Belly-up I have been trying to recover data from it's damaged SATA disk.
I finally got an external cage for the disk, as machines with it installed as a second disk wouldn't boot.  My hope was that although it is clearly corrupt I might be able to mount it to get to the data partition. (it had sep. boot and data partitions) The data partition was ntfs.

I popped it in the usb cage and the the disk made encourageing buzzing noises but did not mount.  here is the output from dmesg:

```

[10936.344196] scsi4 : SCSI emulation for USB Mass Storage devices
[10936.348131] usbcore: registered new interface driver usb-storage
[10936.348571] USB Mass Storage support registered.
[10936.349239] usb-storage: device found at 3
[10936.349245] usb-storage: waiting for device to settle before scanning
[10942.348288] usb-storage: device scan complete
[10947.960055] usb 2-5: USB disconnect, address 3
[10947.962696] scsi 4:0:0:0: Device offlined - not ready after error recovery
[11037.594224] Too big adjustment 32
[11037.614946] Too big adjustment 32

```

Am I on a lost cause here, or is there anyway I can force  a mount of the data partition?

Cheers

---

### Post by kidders on 2009-02-18
Hi there,

You're a bit away from being in a position to mount any filesystems, I'm afraid. It doesn't seem like your system even got as far as searching for a partition table. My guess is the device took too long to reset itself to a ready state, and the kernel got fed up waiting for it.

Your filesystems may not be corrupted at all ... I'd say mechanical damage is preventing the device from functioning properly, which is something you won't be able to do anything about at a software level. :-(

---

### Post by kneewax on 2009-02-18
aww - pants, but not a surprise!

Ah well, its do without or go to one of those big sacry expensive data recovery places I guess!

thanks fro reply!

---

