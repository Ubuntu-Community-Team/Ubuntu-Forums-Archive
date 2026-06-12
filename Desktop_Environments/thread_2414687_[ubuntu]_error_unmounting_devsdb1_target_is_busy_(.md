---
title: "[ubuntu] error unmounting /dev/sdb1: target is busy (udisks-error-quark, 14)"
date: 2019-03-13
forum: Desktop Environments
---

### Post by geek04 on 2019-03-13
So right now I'm trying to make a bootable Ubuntu flash drive to impress my friends, and so far it seemed to work, until when I was trying to unmount my flash drive from /cdrom but i come across the error

```
Error unmounting /dev/sdb1: target is busy (udisks-error-quark,, 14)
```

What I've seen is that I need to unmount the drive or else I wont be able to install it directly on the flash drive.

If you all need me to type in something in terminal I'm happy to.

Any support would help. Thanks! :p

---

### Post by TheFu on 2019-03-14
If any process is using any files or sitting with a PWD inside a directory on the flash drive, then it will be "busy" and cannot be umounted.

If you want help making a live-boot flash device, there is a how-to page just for that.
If you want help umounting storage (umount is the command, not unmount), it cannot be in use.  Certain file systems will always be in use - like the boot and OS partitions. The only way to access them when the partition(s) aren't mounted is to boot from alternate media - an SSD, HDD, flash disk, USB disk, CDROM, DVD, something else.

---

### Post by geek04 on 2019-03-14
Then how can I install it on the flash drive if I can't unmount the drive?

---

### Post by stefan_bahrens on 2019-05-01
> **geek04 said:**
> Then how can I install it on the flash drive if I can't unmount the drive?

This command forced an unmount for me. NOTE - it is umount NOT unmount.
umount -l /PATH/OF/BUSY-DEVICE ....in my case umount -l /dev/sdc

Next I ran the Ubuntu utility called simply "Disks" it came with Ubuntu and is very powerful.
Start it with the unmounted drive plugged in. It will show the drive. Look for the gear wheels
just underneath the drive, click on them and you can select "Check Filesystem" and "Repair
Filesystem". I had to reboot the drive a few times after "Repair" but it worked.

---

### Post by him610 on 2019-05-02
@geek04
One stop application for installing distros on USB drives is *[COLOR="#FF0000"]mkusb[/COLOR]*
Here is a very good tutorial on it....
[https://ubuntuforums.org/showthread.php?t=1958073]("https://ubuntuforums.org/showthread.php?t=1958073")
It is the only application I have used for the past several years. Never had any issues with it.

---

### Post by TheFu on 2019-05-02
> **geek04 said:**
> Then how can I install it on the flash drive if I can't unmount the drive?

Use a different flash drive?

gnome-disks might work, but few experts trust it.  Be very careful. Please.

---

