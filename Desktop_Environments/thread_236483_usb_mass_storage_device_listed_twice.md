---
title: "usb mass storage device listed twice"
date: 2006-08-14
forum: Desktop Environments
---

### Post by stdragon on 2006-08-14
Hi,

I have a USB thumb drive that shows up twice on the desktop when I plug it in, first as "usbdisk" then as "usbdisk-1". When I eject one of them, the other remains but is inaccessible. When I eject the remaining one, it has an error but disappears.

When I run "lsusb" it shows:

```

Bus 003 Device 002: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0c45:1060 Microdia iFlash SM-Direct Card Reader
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

So it's only listed once there. However, in /var/log/messages it does show up twice:

```

Aug 14 20:00:34 localhost kernel: [17770629.368000]   Vendor: USB NAND  Model: FLASH DISK        Rev: 0.30
Aug 14 20:00:34 localhost kernel: [17770629.368000]   Type:   Direct-Access                  ANSI SCSI revision: 02
Aug 14 20:00:34 localhost kernel: [17770629.436000] SCSI device sde: 256000 512-byte hdwr sectors (131 MB)
Aug 14 20:00:34 localhost kernel: [17770629.444000] sde: Write Protect is off
Aug 14 20:00:34 localhost kernel: [17770629.472000] SCSI device sde: 256000 512-byte hdwr sectors (131 MB)
Aug 14 20:00:34 localhost kernel: [17770629.476000] sde: Write Protect is off
Aug 14 20:00:34 localhost kernel: [17770629.476000]  sde: sde1
Aug 14 20:00:34 localhost kernel: [17770629.488000] sd 13:0:0:0: Attached scsi removable disk sde
Aug 14 20:00:34 localhost kernel: [17770629.488000] sd 13:0:0:0: Attached scsi generic sg4 type 0
Aug 14 20:00:34 localhost kernel: [17770629.496000]   Vendor: USB NAND  Model: FLASH DISK        Rev: 0.30
Aug 14 20:00:34 localhost kernel: [17770629.496000]   Type:   Direct-Access                  ANSI SCSI revision: 02
Aug 14 20:00:34 localhost kernel: [17770629.504000] SCSI device sdf: 256000 512-byte hdwr sectors (131 MB)
Aug 14 20:00:34 localhost kernel: [17770629.548000] sdf: Write Protect is off
Aug 14 20:00:34 localhost kernel: [17770629.548000]  sdf: sdf1
Aug 14 20:00:34 localhost kernel: [17770629.596000] sd 13:0:0:1: Attached scsi removable disk sdf
Aug 14 20:00:34 localhost kernel: [17770629.596000] sd 13:0:0:1: Attached scsi generic sg5 type 0

```

As you can see it's there as sde and sdf. Likewise, "mount" shows it twice:

```

/dev/sde1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdf1 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

It also starts a lot of hald-storage-addon processes!

```

27166 ?        S<     0:00 [scsi_eh_11]
27167 ?        S<     0:00 [usb-storage]
27330 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27331 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27354 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27355 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27358 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27359 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27362 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27363 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27719 ?        S<     0:00 [scsi_eh_13]
27720 ?        S<     0:00 [usb-storage]
27767 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27768 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27773 ?        S      0:00 /usr/lib/hal/hald-addon-storage
27774 ?        S      0:00 /usr/lib/hal/hald-addon-storage

```

Can anybody help me out?

---

### Post by aNoble on 2007-02-16
I know it's been a long time since this was posted but I'm having the same problem.

If I boot up with a sdcard in my laptop I'll see it twice on the desktop. If I unmount it or remove it I can't remount it later on.

However, if I boot up with the SD slot empty and then insert the SD card after gnome has started everything seems to work fine.

Any ideas?

---

### Post by gauteh on 2007-12-12
> **aNoble said:**
> I know it's been a long time since this was posted but I'm having the same problem.

If I boot up with a sdcard in my laptop I'll see it twice on the desktop. If I unmount it or remove it I can't remount it later on.

However, if I boot up with the SD slot empty and then insert the SD card after gnome has started everything seems to work fine.

Any ideas?

I have the same problem with my usb harddrive, But it only shows up once in the Computer place in nautilus.

- gaute

---

### Post by matthias_k on 2008-03-16
same problem here. I'm on Feisty. Will this be fixed for Hardy?

---

### Post by pietjanjaap on 2008-03-16
USB thumb drive is possible to see 2 drive's, because on u3 thumb drive there are 2 partitions.
1 with backup program, 2 backup space.

---

### Post by matthias_k on 2008-03-16
My USB drive has only 2 partition, and it only shows up once when being plugged in at runtime. But as the OP said, when you boot the system with the drive in place, there will be two icons instead.

This is clearly a bug, not a feature.

---

