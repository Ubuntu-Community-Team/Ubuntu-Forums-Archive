---
title: "How do I mount this?"
date: 2006-03-14
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-14
I bought a pair of SanDisk Cruzer Micro 256Mb flash drives. I plugged one of them into my USB slot and up popped an icon on my desktop along with nautilus opening to /media/usbdisk. Talk about simple and easy! I love this!

Now, here's what I want to do. I have a script that contains:

```

#! /bin/bash
cd /home
tar -cjf /home/backups/current.home.tar.bz2 myuser
mv /home/backups/current.home.tar.bz2 /home/backups/`date +%Y%m%d`.myuser.tar.bz2

```

This is the backup scheme I use to backup everything in $HOME and it adds the current date to the filename. This works great for me. However, now that I have the flash drives, I'd like to put a copy of the current backup on the flash drive in case my hard drive dies. So, what I need to do is:
1) mount the flash drive
2) make the backup
3) copy the current backup to the flashdrive
4) unmount the flashdrive

I unmounted the flashdrive and tried to mount it again with "sudo mount /dev/sda /media/usbdisk" and got "mount: No medium found" and it didn't mount. Here is the output of dmseg:

```

[4317372.993000] usb 4-2: new high speed USB device using ehci_hcd and address 6
[4317373.072000] scsi4 : SCSI emulation for USB Mass Storage devices
[4317373.074000] usb-storage: device found at 6
[4317373.074000] usb-storage: waiting for device to settle before scanning
[4317378.074000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.1
[4317378.074000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4317378.078000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4317378.079000] sda: Write Protect is off
[4317378.079000] sda: Mode Sense: 03 00 00 00
[4317378.079000] sda: assuming drive cache: write through
[4317378.085000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4317378.086000] sda: Write Protect is off
[4317378.086000] sda: Mode Sense: 03 00 00 00
[4317378.086000] sda: assuming drive cache: write through
[4317378.086000]  /dev/scsi/host4/bus0/target0/lun0: p1
[4317378.089000] Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
[4317378.091000] usb-storage: device scan complete

```

I just assumed it was /dev/sda but I could be wrong.

**Question 1**
How exactly do I mount this new flash drive so I can use my backup script?

**Question 2**
If, for some reason, my box loses power while the flash drive is mounted, will the power outage destroy the files on the flash drive because it wasn't unmounted properly before the box lost power?

---

### Post by ardchoille on 2006-03-15
Here is what I found. When I have automounting turned on in gnome, gnome automounts /dev/sda1 to /media/usbdisk. When I unmount it via the right-click menu on the desktop volume, then I cannot manually mount it again using "sudo mount /dev/sda1 /media/usbdisk". However, when I turn off automounting, then I can successfully mount it using "sudo mount /dev/sda1 /media/usbdisk" and unmount it. I am guessing that hal is messing something up somehow. No problem, I'll keep automounting turned off so my script will work. Problem solved :)

---

