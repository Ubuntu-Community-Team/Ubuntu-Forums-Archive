---
title: "Create ISO from USB drive"
date: 2009-01-18
forum: General Help
---

### Post by Pulsewave on 2009-01-18
Hi World.
.
I have create a USB boot disk of Ubuntu 8.10 on a 4 GB flash disk.
.
I have customized the install.
.
Now i would like to create a ISO file of the USB disk.
.
Anyone have any ideas if it is possible to create an ISO file of USB flash disk or any other method to create a backup of my USB flash that can be restored to any other flash drives.
.
Thanks In Advance

---

### Post by HalPomeranz on 2009-01-18
You can use dd for this.  In the example commands below, I'm assuming your USB device is recognized by the system as /dev/sdb.  You should make sure that this is the case before executing any of the commands below, because if you get the device name wrong, the second command below will end up overwriting the wrong device and destroying your data.

To make an image from your existing USB setup and write it to the file usb-image.iso:

```

sudo dd if=/dev/sdb of=usb-image.iso

```

You could now remove your current USB device and connect an empty device, which the system should again see as /dev/sdb.  To copy the usb-image.iso file onto the new device:

```

sudo dd if=usb-image.iso of=/dev/sdb

```

Again it is EXTREMELY IMPORTANT that you make sure you're using the correct device name before executing the command above.  Otherwise you run the risk of clobbering the data on some other disk device that may be critical to your system.

---

### Post by Pulsewave on 2009-01-18
Thanks Hal, ill try that.

---

### Post by cpeee on 2009-05-20
Sorry for responding to an old thread. I'm looking to do the same thing. Do u dd the entire device or the partition of the device? Reason why I asked is that, I may need to re-create the usb-drive to a totally different (in size) one. Example, my original USB is 2GB, I would like the .iso to be replicated/created on a 4GB drive, would dd /dev/sdb have the same effect as dd /dev/sdb1? assume I only have 1 partition on the original drive. Thanks!

---

### Post by colau on 2009-05-20
> **HalPomeranz said:**
> You can use dd for this.  In the example commands below, I'm assuming your USB device is recognized by the system as /dev/sdb.  You should make sure that this is the case before executing any of the commands below, because if you get the device name wrong, the second command below will end up overwriting the wrong device and destroying your data.

To make an image from your existing USB setup and write it to the file usb-image.iso:

```

sudo dd if=/dev/sdb of=usb-image.iso

```

You could now remove your current USB device and connect an empty device, which the system should again see as /dev/sdb.  To copy the usb-image.iso file onto the new device:

```

sudo dd if=usb-image.iso of=/dev/sdb

```

Again it is EXTREMELY IMPORTANT that you make sure you're using the correct device name before executing the command above.  Otherwise you run the risk of clobbering the data on some other disk device that may be critical to your system.

Nice tip and thanks for your signature link as well.

---

### Post by Brandon Williams on 2009-05-20
> **cpeee said:**
> Sorry for responding to an old thread. I'm looking to do the same thing. Do u dd the entire device or the partition of the device? Reason why I asked is that, I may need to re-create the usb-drive to a totally different (in size) one. Example, my original USB is 2GB, I would like the .iso to be replicated/created on a 4GB drive, would dd /dev/sdb have the same effect as dd /dev/sdb1? assume I only have 1 partition on the original drive. Thanks!

If you use if=/dev/sdb1 instead of if=/dev/sdb, then yes, you will create an image of the partition. If you have a larger USB drive, you can simply create a correctly sized partition on that drive and then copy your image to just that partition using the partition's device name as the of= parameter, as in of=/dev/sdb1.

---

### Post by russet_wolf on 2009-11-12
Sorry for replying to this old post, but is there any way to save the ISO to the hard drive instead of burning it to a new device right away?

---

### Post by wilee-nilee on 2009-11-12
> **russet_wolf said:**
> Sorry for replying to this old post, but is there any way to save the ISO to the hard drive instead of burning it to a new device right away?

You can probably drag the whole thing into file, but whether it is usable again as it is on the USB device is probably in question here. I suspect that is why there are special programs to burn it. But it might be a good reference tool in case you want to access the added software for documenting the installs.

You also should be aware of the daily builds of Ubuntu, these are the updated version up to the date of the fixes of software issues,and are formatted to a iso for a CD burn.

---

### Post by Siljrath on 2009-12-18
i'm fairly familiar with dd, i'm looking for a way to achieve this without copying all the empty space too.

i am also familiar with remastersys, but this is not an option this time for me.

what other methods are there?

someone suggested there's an iso-builder, i tried searching for such a thing several ways, but this thread was best i came up with.

---

### Post by satir.satir on 2011-04-17
to view progres i use tee

```
sudo dd if=/dev/sdf of=usb-image.iso | tee usb-image.txt
```

---

### Post by kumsy on 2011-07-29
use iso master to create an iso of the usb drive.search and download it from synaptic package manager or ubuntu software centre.choose the pendrive directory and choose add.:D

---

