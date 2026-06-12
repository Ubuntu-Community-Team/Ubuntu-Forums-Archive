---
title: "Can't unmount amazon kindle 2"
date: 2009-03-27
forum: General Help
---

### Post by skream on 2009-03-27
I'm using: 
ubuntu 8.04 
Asus EEE 701 4g 
kernel 2.6.24-21-eeepc


Im having problems unmounting my Amazon Kindle 2. Upon plugging the kindle into a usb port it mounts perfectly well and i can do whatever i need to do while it is acting as removable storage.  I just can't get it to unmount so that i can read on it while its charging.  I have tried sudo umount /media/Kindle but its still appears to be mounted, but is unaccessible.

here is my /var/log/messages output when i plug it in:
Mar 27 17:05:50 skream-laptop kernel: [88456.369039] usb 5-2: new high speed USB device using ehci_hcd and address 11

Mar 27 17:05:50 skream-laptop kernel: [88456.428949] usb 5-2: configuration #1 chosen from 1 choice

Mar 27 17:05:50 skream-laptop kernel: [88456.481544] scsi6 : SCSI emulation for USB Mass Storage devices

Mar 27 17:05:56 skream-laptop kernel: [88457.623513] scsi 6:0:0:0: Direct-Access     Kindle   Internal Storage 0100 PQ: 0 ANSI: 2

Mar 27 17:05:56 skream-laptop kernel: [88457.642131] sd 6:0:0:0: [sdc] 3121328 512-byte hardware sectors (1598 MB)

Mar 27 17:05:56 skream-laptop kernel: [88457.729194] sd 6:0:0:0: [sdc] Write Protect is off

Mar 27 17:05:56 skream-laptop kernel: [88457.734992] sd 6:0:0:0: [sdc] 3121328 512-byte hardware sectors (1598 MB)

Mar 27 17:05:56 skream-laptop kernel: [88457.801114] sd 6:0:0:0: [sdc] Write Protect is off

Mar 27 17:05:56 skream-laptop kernel: [88457.801204]  sdc: sdc1

Mar 27 17:05:56 skream-laptop kernel: [88458.374882] sd 6:0:0:0: [sdc] Attached SCSI removable disk

Mar 27 17:05:56 skream-laptop kernel: [88458.375201] sd 6:0:0:0: Attached scsi generic sg2 type 0






When i try to unmount it, nothing changes in the /var/log/messages, i cant access the kindle, and the kindle still says its being used as removable media.  Seems like its just half *** unmounting.

---

### Post by modmadmike on 2009-03-27
try ```
sudo umount /dev/(insert kindle device address here)
```

---

### Post by modmadmike on 2009-03-27
> **modmadmike said:**
> try ```
sudo umount /dev/(insert kindle device address here)
```

oh or you can do ```
sudo umount (mountpoint goes here)
```

---

### Post by modmadmike on 2009-03-27
> **modmadmike said:**
> try ```
sudo umount /dev/(insert kindle device address here)
```

ok its ```
sudo umount /dev/sdc1
``` or ```
sudo umount /dev/sdc
```

---

### Post by skream on 2009-03-27
neither worked, same results.

---

### Post by bayonetblaha on 2009-04-14
sudo eject /dev/sdb1

---

### Post by soltanis on 2009-04-14
Try to do a forced unmount

```

sudo umount -f /dev/sdc

# if that doesn't work do a lazy unmount

sudo umount -l /dev/sdc

```

The second command will hopefully execute, unmounting the device and cleaning up the filesystem later.

If those still dont work, you might want to try the -r option, which attempts to remount read-only, or you might just unplug the kindle...probably a bad idea though.

---

### Post by bayonetblaha on 2009-04-14
umount won't work to switch the kindle to power-only.  'eject' is the correct solution. I just tried it.

[http://iamyouruser.blogspot.com/2009/03/ubuntu-eject-kindle.html](http://iamyouruser.blogspot.com/2009/03/ubuntu-eject-kindle.html)

---

