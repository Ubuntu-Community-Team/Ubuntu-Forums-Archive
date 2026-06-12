---
title: "External Hard Drive"
date: 2006-08-31
forum: Desktop Environments
---

### Post by ashari on 2006-08-31
Greetings!

I am happy to be a new member of Ubuntu community!  I have been
using Ubuntu 6.06 LTS for the last couple of days and so far it 
has been great!  

I had one of those external hard drives via USB connected 
to the Ubuntu box.  In the middle of things, the power got
interrupted.  Now when I reconnect, the drive is spinning
but Ubuntu won't auto mount it.

Is all the data irrecovably lost?  Or is there some thing
that I can try to get the data.  I think the only other choice
is to reformat the drive.

Any helpful suggestions appreciated.

dmesg output:
```

[17179679.660000] SCSI subsystem initialized
[17179679.720000] Initializing USB Mass Storage driver...
[17179679.724000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179679.724000] usb-storage: device found at 2
[17179679.724000] usb-storage: waiting for device to settle before scanning
[17179679.724000] usbcore: registered new driver usb-storage
[17179679.724000] USB Mass Storage support registered.
[17179690.448000] usb 4-2: USB disconnect, address 2
[17179690.448000]  0:0:0:0: scsi: Device offlined - not ready after error recovery
[17179690.448000] usb-storage: device scan complete
[17179972.340000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179972.340000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179972.340000] ide: failed opcode was: unknown
```


Regards.

ashari

---

### Post by millerdc on 2006-08-31
try using fdisk to see if it can list it.

sudo fdisk -l

if it shows the drive try mounting it manually like so.

sudo mkdir /mnt/tmp

sudo mount /dev/sda1 /mnt/tmp

---

### Post by ashari on 2006-08-31
Hi,

Output from fdisk -l doesn't show the drive.  Neither
does the dmesg output.

Thanks.

ashari

---

### Post by df3n5 on 2006-08-31
Try restarting the computer with the external hard drive on. The hard drive should auto mount.

---

### Post by ashari on 2006-08-31
Hmm...  Tried rebooting the machine with the external
drive attached.  It didn't work as I feared  since dmesg
is clearly reporting the checksum mismatch.  

Anyways, thanks and appreciate your suggestion.

I have a long weekend coming so I can try more of other
suggestions from this friendly community 8-}

Regards.

ashari

---

### Post by ashari on 2006-08-31
After googling a bit and re-reading the dmesg output, 
I now know that (a) there is an impending hard drive 
crash as may be indicated by the checksum failure errors 
and (b) the mass storage SCSI device is unrecognized.

Still looking...

ashari

---

### Post by UniRecovery on 2006-09-01
Seemingly, the drive has either "Bad sectors" or physical internal damage. 
Avoid rebooting from it as more damage is bound to occur on the drive if you want your data back. You need to carry out data recovery on the hard disk. Get in touch with us [http://www.unirecovery.co.uk](http://www.unirecovery.co.uk)

---

