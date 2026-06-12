---
title: "Devices only mounting once per boot"
date: 2006-02-28
forum: Desktop Environments
---

### Post by blindspy on 2006-02-28
I can mount all my usb devices fine but if I unmount them and try to mount it again later, it will not mount. My system cannot allocate space once something has been mounted already. Dmesg has this output:

```
[66300.347658] usb 4-1: new high speed USB device using ehci_hcd and address 4
[66300.498558] kmem_cache_create: duplicate cache scsi_cmd_cache
[66300.498602]  [<c0164aac>] kmem_cache_create+0x3bc/0x6f0 (8)
[66300.498619]  [<c0183c28>] __d_lookup+0x88/0x120 (32)
[66300.498624]  [<c013799f>] _spin_lock_init+0x2f/0x40 (4)
[66300.498634]  [<f0ae039d>] scsi_setup_command_freelist+0x8d/0x120 [scsi_mod] (24)
[66300.498677]  [<f0ae1c47>] scsi_host_alloc+0x217/0x390 [scsi_mod] (40)
[66300.498699]  [<f0e36ea1>] storage_probe+0x31/0x270 [usb_storage] (36)
[66300.498726]  [<f08c80d4>] usb_probe_interface+0x74/0xa0 [usbcore] (40)
[66300.498765]  [<c0247bf6>] driver_probe_device+0x46/0xe0 (20)
[66300.498775]  [<c0247c90>] __device_attach+0x0/0x10 (28)
[66300.498779]  [<c02472ad>] bus_for_each_drv+0x5d/0x80 (4)
[66300.498790]  [<c0247d0a>] device_attach+0x6a/0x90 (44)
[66300.498796]  [<c0247c90>] __device_attach+0x0/0x10 (16)
[66300.498801]  [<c02473f5>] bus_add_device+0x35/0xd0 (12)
[66300.498806]  [<c024b5e6>] device_pm_add+0x86/0xa0 (8)
[66300.498816]  [<c0246400>] device_add+0x120/0x1a0 (24)
[66300.498826]  [<f08d11fd>] usb_set_configuration+0x24d/0x4e0 [usbcore] (36)
[66300.498861]  [<f08caee3>] usb_new_device+0x133/0x1d0 [usbcore] (88)
[66300.498884]  [<f08cc258>] hub_port_connect_change+0x368/0x420 [usbcore] (40)
[66300.498906]  [<f08c9487>] clear_port_feature+0x57/0x60 [usbcore] (32)
[66300.498929]  [<f08cc610>] hub_events+0x300/0x490 [usbcore] (40)
[66300.498952]  [<c01332db>] finish_wait+0x4b/0x70 (44)
[66300.498961]  [<f08cc7a0>] hub_thread+0x0/0xf0 [usbcore] (16)
[66300.498978]  [<f08cc7b5>] hub_thread+0x15/0xf0 [usbcore] (4)
[66300.498995]  [<c0133300>] autoremove_wake_function+0x0/0x60 (12)
[66300.499003]  [<c0132dd6>] kthread+0xb6/0xc0 (24)
[66300.499010]  [<c0132d20>] kthread+0x0/0xc0 (24)
[66300.499016]  [<c01013f9>] kernel_thread_helper+0x5/0xc (16)
[66300.499024] usb-storage: Unable to allocate the scsi host
[66300.499027] usb-storage: probe of 4-1:1.0 failed with error -12
```

Rebooting allows me to mount stuff once.

---

### Post by hectorC on 2006-07-16
many months later... I have exactly the same problem. Anyone found a solution to this?


mmm... didn't see this is Breezy... I'm using Dapper.

Thanks!

Hector.

---

### Post by blindspy on 2006-07-16
The way I solved the problem was to use the Ubuntu stock kernel. Something in my custom kernel (I never figured out what) was causing this problem and it was fixed in the stock kernel.

What kernel are you running?

---

### Post by hectorC on 2006-07-17
a custom kernel... mmmm

that should be the source of the problem. and I really need to use this kernel because I use Ubuntu for audio so I have to compile a kernel with realtime patches... anyway... one of the many patches that are applied to the stuck Ubuntu kernel should be the one that fixes this, but who knows which!

thanks

---

