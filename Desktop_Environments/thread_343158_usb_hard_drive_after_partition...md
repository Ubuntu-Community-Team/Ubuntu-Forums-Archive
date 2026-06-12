---
title: "usb hard drive after partition.."
date: 2007-01-21
forum: Desktop Environments
---

### Post by Mia_tech on 2007-01-21
guys after installing a new usb hard drive, I have partitioned the hd, and ubuntu detects it and mounted as /media/usbdisk, but I'm not able to create any files, yes I know is a permission issue, so I presume, after opening qtparted it shows the usb hard drive as /dev/sda, but it's also showing as /dev/sda1 under system monitor, any ways I issued " sudo chmod ugo+rwx /dev/sda1, no errors were returned but still were unable to make any changes.
any help 

Thanks

---

### Post by taurus on 2007-01-21
What filesystem is on /dev/sda1?  And besides, you need to change the permissions to the mount point, /media/usbdisk, not the device itself.

---

### Post by Mia_tech on 2007-01-21
> **taurus said:**
> What filesystem is on /dev/sda1?  And besides, you need to change the permissions to the mount point, /media/usbdisk, not the device itself.

file system is ext2, and yes I also tried that sudo chmod ugo+rwx /media/usbdisk, and didn't work either, then again no errors, I umounted -a all drives, and mount -a back again just in case no luck

---

### Post by taurus on 2007-01-21
For now, I will assume your login name to your machine is **mia** so change it to whatever it is.

```
sudo chown -R **mia**:**mia** /media/usbdisk
sudo chmod -R 755 /media/usbdisk
```
Now, see if you can write or save stuff to /media/usbdisk.

---

### Post by Mia_tech on 2007-01-21
got it working for some estrange reason it took for me to reboot the system to be able to create files from the GUI, after issuing the sudo chmod ugo+rwx /media/usbdisk, I was able from the CLI
to create and delete files, but not from the GUI, after umount -a and mount -a, same result, it took for me to reboot the system.......go figure, but thanks for the help

---

### Post by Athropos on 2007-01-21
> **Mia_tech said:**
> got it working for some estrange reason it took for me to reboot the system to be able to create files from the GUI, after issuing the sudo chmod ugo+rwx /media/usbdisk, I was able from the CLI
to create and delete files, but not from the GUI, after umount -a and mount -a, same result, it took for me to reboot the system.......go figure, but thanks for the help

I got the same error with my own external HDD. Permissions are stored in some sort of cache, that's why the GUI doesn't let you create files.

---

