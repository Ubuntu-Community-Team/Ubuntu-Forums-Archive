---
title: "unable to mount usb drive (mp3 player) twice"
date: 2006-07-16
forum: Desktop Environments
---

### Post by hectorC on 2006-07-16
Someone posted the same problem but with Breezy... mine is with Dapper:

I can mount my USB drive (iriver T30) fine but if I unmount it and try to mount it again later, it will not mount. The system cannot allocate space once something has been mounted already.

here is my Dmesg:

[ 5710.831312] usb 5-5: USB disconnect, address 6
[ 5759.672410] usb 5-5: new high speed USB device using ehci_hcd and address 7
[ 5759.787209] kmem_cache_create: duplicate cache scsi_cmd_cache
[ 5759.787231]  [<c0159f99>] kmem_cache_create+0x2f8/0x686 (8)
[ 5759.787263]  [<c013088d>] _spin_lock_init+0x2f/0x33 (44)
[ 5759.787282]  [<f8c64342>] scsi_setup_command_freelist+0x8d/0x117 [scsi_mod] (24)
[ 5759.787319]  [<f8c65a4c>] scsi_host_alloc+0x217/0x38d [scsi_mod] (40)
[ 5759.787349]  [<f8f37995>] storage_probe+0x31/0x256 [usb_storage] (36)
[ 5759.787382]  [<f88a30af>] usb_probe_interface+0x68/0x8a [usbcore] (40)
[ 5759.787407]  [<c0240bf2>] driver_probe_device+0x3d/0xa1 (20)
[ 5759.787426]  [<c0240c56>] __device_attach+0x0/0x5 (28)
[ 5759.787429]  [<c02403dc>] bus_for_each_drv+0x5b/0x7b (4)
[ 5759.787456]  [<c0240cb9>] device_attach+0x5e/0x6f (44)
[ 5759.787466]  [<c0240c56>] __device_attach+0x0/0x5 (16)
[ 5759.787475]  [<c0240509>] bus_add_device+0x29/0xa6 (12)
[ 5759.787481]  [<c0243e3a>] device_pm_add+0x7d/0x86 (8)
[ 5759.787497]  [<c023f6e5>] device_add+0x108/0x17d (24)
[ 5759.787523]  [<f88ab982>] usb_set_configuration+0x2a1/0x4ef [usbcore] (36)
[ 5759.787595]  [<f88a5976>] usb_new_device+0x115/0x1a2 [usbcore] (80)
[ 5759.787631]  [<f88a6fda>] hub_port_connect_change+0x363/0x434 [usbcore] (40)
[ 5759.787663]  [<f88a41a7>] clear_port_feature+0x57/0x5b [usbcore] (32)
[ 5759.787699]  [<f88a73c4>] hub_events+0x319/0x4a4 [usbcore] (40)
[ 5759.787730]  [<c012bfe1>] finish_wait+0x42/0x53 (36)
[ 5759.787742]  [<f88a754f>] hub_thread+0x0/0xe5 [usbcore] (16)
[ 5759.787757]  [<f88a7563>] hub_thread+0x14/0xe5 [usbcore] (4)
[ 5759.787775]  [<c012bff2>] autoremove_wake_function+0x0/0x4b (12)
[ 5759.787791]  [<c012bb89>] kthread+0x9d/0xa1 (24)
[ 5759.787806]  [<c012baec>] kthread+0x0/0xa1 (24)
[ 5759.787816]  [<c01013b9>] kernel_thread_helper+0x5/0xb (16)
[ 5759.787832] usb-storage: Unable to allocate the scsi host
[ 5759.787835] usb-storage: probe of 5-5:1.0 failed with error -12


And this is dmesg at the first mount (the only one I'm able to do without rebooting):

[   89.612529] usb 5-5: new high speed USB device using ehci_hcd and address 4
[   89.834788] Initializing USB Mass Storage driver...
[   89.836011] scsi0 : SCSI emulation for USB Mass Storage devices
[   89.836329] usb-storage: device found at 4
[   89.836332] usb-storage: waiting for device to settle before scanning
[   89.836566] usbcore: registered new driver usb-storage
[   89.836675] USB Mass Storage support registered.
[   94.825341]   Vendor: iriver    Model: T30 Pure          Rev: 1.00
[   94.825354]   Type:   Direct-Access                      ANSI SCSI revision: 02
[   94.825666] usb-storage: device scan complete
[   94.857120] SCSI device sda: 2041856 512-byte hdwr sectors (1045 MB)
[   94.858239] sda: Write Protect is off
[   94.858337] sda: Mode Sense: 03 00 00 00
[   94.858433] sda: assuming drive cache: write through
[   94.872829] SCSI device sda: 2041856 512-byte hdwr sectors (1045 MB)
[   94.873950] sda: Write Protect is off
[   94.874105] sda: Mode Sense: 03 00 00 00
[   94.874206] sda: assuming drive cache: write through
[   94.874306]  sda: unknown partition table
[   94.881076] sd 0:0:0:0: Attached scsi removable disk sda
[   94.889708] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   95.114841] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!



thans in advance for any help!

Hector

---

### Post by cptnapalm on 2006-07-17
Mine does something kindo of odd if I unmount it, sometimes.  Mine is normally /dev/sdb1 but I have when remounting it, seen it become /dev/sdc1.  It works just fine, but it is odd.

---

### Post by sinaen on 2006-08-29
i have the same problem, to mee it seems that the system doesnt have time to flush its usb-interface. if you wait a while longer it should reappear at /dev/sdb1 for an example

---

### Post by sinaen on 2006-08-29
my problem is with an iriver ifp-799. with ums firmware (the one that makes it an ordinary usb-disk. i can put it in. then i must make an partitiontable. and format it. (fat16) to make it recognizable. when i pull it out and later on put it back in again. i cannot se the device. the standard device is there /dev/sda and /dev/sg0 you all know that /dev/sg0 isnt an real device. so i go into the partititonmanager again.  
Qtparted. and there i see that it has files on it, but i cannot access it. until i format. then the /dev/sda1 device pop up and ill be able to mount it :( its such a drag.

---

