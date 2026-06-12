---
title: "My external USB drive has disappeared"
date: 2006-06-27
forum: Desktop Environments
---

### Post by cward002 on 2006-06-27
Hi I connected an external USB drive and everything worked. I want to use it to back up my dapper system so I wanted to format it as ext3. I used GParted. The only problem is that I set a disklabel and now my system does not automount the drive. I typed a command (can't remember which) and the drive is listed but it just won't automount. is there  a way to recover from this?

Thanks

Colin

---

### Post by taurus on 2006-06-27
See if you can mount it by hand, from a terminal (Applications -> Accessories -> Terminal).
```

sudo mkdir /mnt/usb
sudo mount -t ext3 /dev/sda1 /mnt/usb
(assuming that /dev/sda1 is your USB drive...)
ls -la /mnt/usb

```

---

### Post by cward002 on 2006-06-27
Thanks I'll give it  a shot tonight when I'm in front of my machine.

Colin

---

### Post by charafantah on 2006-06-27
hi, 
i got the same problem, i can mount the device manually and i can use it just fine

but Kubuntu(dapper) doesnt automount it, its the same for cdrom usb drives 

i tried to reinstall pmount autofs,,but its still the same....

---

### Post by cward002 on 2006-06-27
Hi I tried it but this is what I got I guess my USB hard drive isnt /dev /sb0. is there a way to find out what it is called

thanks 

Colin

---

### Post by cward002 on 2006-06-27
I got something along the lines of "special device sb0 does not exist. Is there a way to determine what the device is called?

Thanks

Colin

---

### Post by rsay on 2006-06-28
You can look at dmesg to get an idea of what is happening.

```
#dmesg | tail --lines=20
[17213128.140000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17213128.288000] usb 4-1: not running at top speed; connect to a high speed hub
[17213128.448000] SCSI subsystem initialized
[17213128.488000] Initializing USB Mass Storage driver...
[17213128.488000] scsi0 : SCSI emulation for USB Mass Storage devices
[17213128.488000] usb-storage: device found at 2
[17213128.488000] usb-storage: waiting for device to settle before scanning
[17213128.488000] usbcore: registered new driver usb-storage
[17213128.492000] USB Mass Storage support registered.
[17213133.504000]   Vendor: USB 2.0   Model: Storage Device    Rev: 0100
[17213133.504000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17213133.520000] usb-storage: device scan complete
[17213133.544000] Driver 'sd' needs updating - please use bus_type methods
[17213133.556000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17213133.556000] sda: assuming drive cache: write through
[17213133.572000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17213133.572000] sda: assuming drive cache: write through
[17213133.572000]  sda: sda1
[17213133.600000] sd 0:0:0:0: Attached scsi disk sda
[17213133.612000] sd 0:0:0:0: Attached scsi generic sg0 type 0

```
The lines near the end show that my drive is sda with the first(only) partition as sda1

---

### Post by cward002 on 2006-06-28
Thanks, I am at work now, but I will give this a shot tonight.

Colin

---

### Post by cward002 on 2006-06-28
I tried the dmesg command and this is what came back with the HD connected as well as disconnected:

[17179607.540000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179607.540000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179608.876000] eth0: no IPv6 routers present
[17179609.072000] Bluetooth: Core ver 2.8
[17179609.072000] NET: Registered protocol family 31
[17179609.072000] Bluetooth: HCI device and connection manager initialized
[17179609.072000] Bluetooth: HCI socket layer initialized
[17179609.152000] Bluetooth: L2CAP ver 2.8
[17179609.152000] Bluetooth: L2CAP socket layer initialized
[17179609.188000] Bluetooth: RFCOMM socket layer initialized
[17179609.188000] Bluetooth: RFCOMM TTY layer initialized
[17179609.188000] Bluetooth: RFCOMM ver 1.7
[17179614.904000] ath0: no IPv6 routers present
[17179881.400000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179881.400000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179881.400000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17238478.884000] ibm_acpi: ec object not found
[17374098.888000] usb 4-1: USB disconnect, address 2
[17456977.328000] cdrom: open failed.
[17456977.332000] cdrom: open failed.

thanks for your help

---

### Post by cward002 on 2006-06-29
well I think maybe we are making progress(?) The disks manager applet now sees my device(sda) but it cannot access it. (filesystem not recognized). dmesg still doesn't see it though.

---

