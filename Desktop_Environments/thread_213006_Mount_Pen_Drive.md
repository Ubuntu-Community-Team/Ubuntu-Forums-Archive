---
title: "Mount Pen Drive"
date: 2006-07-10
forum: Desktop Environments
---

### Post by root06 on 2006-07-10
Hi everybody,

I have a Mini Traveldrive 512MB, and I cannot get it to mount on my installation of Ubuntu 6.06. If I plug it in before boot and use the LiveCD it works just fine, but if I plug it in at boot, or any time after it, and start up from my hard drive, it does not mount. I have tried various mount commands, all of them failing:


mount /dev/sda0
mount /dev/sda1

mount /dev/sdb0
mount /dev/sdb1

mount /dev/scsi0
mount /dev/scsi1

It will not automount either. In my settings I have to box checke d for automaticly mount removable media when hot-plugged. I do not have internet access on this machine, so please do not ask for my dmsg unless you really think it can help as I would have to manually copy each line.

---

### Post by x64Jimbo on 2006-07-10
the mount command needs a directory that it can bind the filesystem to. Also, you will need to specify the filesystem type, since it is not a Linux filesystem. For instance, since it's a USB flash drive, it should probably look like this:
sudo mkdir /mnt/usb
that's the command to make a special directory for the device to mount to.
sudo mount -t vfat /dev/sda1 /mnt/usb
that should mount the device /dev/sda1 to the directory /mnt/usb with the vfat filesystem specification. Hope that helps.

---

### Post by root06 on 2006-07-11
I'm sorry, the full commands I used did have /mnt after the path to the device. However, I have tried mounting every block device in the /dev folder (hdc, sda, sdb, cdrom) but to no avail. The problem is not where the device is, but how to get it there. In Fedora, the light would turn on as soon as I plugged it in but before I mounted it. Now, the device is not being registered at all in any devices in the /dev folder. Here is a line from dmesg about the pen drive:

 usb 1-2: new full speed usb device using uhci-hcd and address 38


I really need to figure this out soon because without a pen drive the computer is compleetly isolated, and therfore useless for programming.

---

### Post by x64Jimbo on 2006-07-13
If you have the device plugged in, you can open a partition manager and use it to determine the device name. From there you should be able to do it. Also, make sure that you are putting that filesystem type flag in there like I said before. Without that, nothing will work.

---

### Post by ahh_dee on 2006-07-13
it should work if your fstab looks like this 


```
/dev/sda1       /mnt/usb        auto    user,noauto   0   0
```

---

### Post by someusernoob on 2006-07-13
My fstab line looked like this
```

/dev/sda1	/media/usb	vfat	rw,user,noauto,sync,noatime	0	0

```

But if you can, try to get pmount on the system. This automaticly mounted my usb stick when inserted. You have to remove the mount line from your fstab, otherwise it could conflict with each other.

---

