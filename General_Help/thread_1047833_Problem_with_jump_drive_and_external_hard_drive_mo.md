---
title: "Problem with jump drive and external hard drive mounting"
date: 2009-01-22
forum: General Help
---

### Post by MrKenmore on 2009-01-22
Hi everyone!!!  I have an external USB Seagate 1TB external hard drive EXT2 that I use for backup purposes.  Since I run rsync only occasionally, it is unplugged most of the time.  I have the fstab set up as:

/dev/sdc1	/home/fmn/seagate_external_hd	ext2 user,suid,dev,exec,rw	0	0

The problem is that when I try to plug in any other USB drive (a pen/jump drive for instance) I get an error that it can't mount.  What I think is happening is that it is trying to mount it the same as the Seagate drive but nothing matches.

Now the kicker is this error only happens when the external hard drive is unplugged.  When the Seagate is plugged in and then I plug in the jump drive, all is well.

Thanks for any help.

My error log is below:

Jan 22 20:47:19 mother kernel: [300730.492061] usb 5-5: new high speed USB device using ehci_hcd and address 2
Jan 22 20:47:19 mother kernel: [300730.637074] usb 5-5: configuration #1 chosen from 1 choice
Jan 22 20:47:19 mother kernel: [300730.746424] usbcore: registered new interface driver libusual
Jan 22 20:47:19 mother kernel: [300730.769742] Initializing USB Mass Storage driver...
Jan 22 20:47:19 mother kernel: [300730.777173] scsi8 : SCSI emulation for USB Mass Storage devices
Jan 22 20:47:19 mother kernel: [300730.777471] usbcore: registered new interface driver usb-storage
Jan 22 20:47:19 mother kernel: [300730.777479] USB Mass Storage support registered.
Jan 22 20:47:24 mother kernel: [300735.779548] scsi 8:0:0:0: Direct-Access     Memorex  TRAVELDRIVE 005B PMAP PQ: 0 ANSI: 0 CCS
Jan 22 20:47:25 mother kernel: [300736.001618] sd 8:0:0:0: [sdc] 3913728 512-byte hardware sectors (2004 MB)
Jan 22 20:47:25 mother kernel: [300736.004872] sd 8:0:0:0: [sdc] Write Protect is off
Jan 22 20:47:25 mother kernel: [300736.015749] sd 8:0:0:0: [sdc] 3913728 512-byte hardware sectors (2004 MB)
Jan 22 20:47:25 mother kernel: [300736.018873] sd 8:0:0:0: [sdc] Write Protect is off
Jan 22 20:47:25 mother kernel: [300736.023808]  sdc: sdc1
Jan 22 20:47:25 mother kernel: [300736.026209] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Jan 22 20:47:25 mother kernel: [300736.028160] sd 8:0:0:0: Attached scsi generic sg3 type 0
Jan 22 20:47:25 mother kernel: [300736.636683] VFS: Can't find an ext2 filesystem on dev sdc1.
Jan 22 20:51:20 mother kernel: [300971.702102] usb 5-5: USB disconnect, address 2

---

### Post by svrkispm on 2009-01-22
try to use volume id instead of device node in fstab

---

### Post by MrKenmore on 2009-01-22
That's a pretty good idea.

I'll try that.

---

### Post by MrKenmore on 2009-01-22
Totally worked!!  Thanks a million.

---

