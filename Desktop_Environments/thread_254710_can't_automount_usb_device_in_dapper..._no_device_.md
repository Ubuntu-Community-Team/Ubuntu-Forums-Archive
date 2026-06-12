---
title: "can't automount usb device in dapper... no device created"
date: 2006-09-10
forum: Desktop Environments
---

### Post by monkblah on 2006-09-10
Hi,

I have a usb flash card reader attached to my computer. When I used Hoary, if I inserted a flash card into it, it was automounted, and kubuntu created an icon for it on my desktop. 

Now I have upgraded to Dapper, and it no longer works. It seems to be the case that no /dev device file exists for the device. 

If I insert a card into the reader and reboot my machine, a device is created, and the disk is mounted. If I remove the card and reboot, however, the device file no longer exists when ubuntu comes back on, and if I insert a card one is not created.

How can I tell Dapper ubuntu to make this work, so that when I insert a card into the reader, it gets automounted, like it used to work before?

------------------------------------
When booted with card inserted:
```

$ ls -l /dev/sda*
brw-rw---- 1 root plugdev 8, 0 2006-09-10 07:48 /dev/sda
brw-rw---- 1 root plugdev 8, 1 2006-09-10 11:48 /dev/sda1
$

```

From my /etc/fstab:
```

/dev/sda1       /media/cardreader0 vfat auto,user 0 0

```

---

### Post by Big_J on 2006-09-10
I have a similar problem, but mine doesn't mount if I reboot.. I used the flash drive and the card reader on many distros and ubuntu is the only one giving me trouble with it; I can't even manually mount any usb device because they aren't even detected on ubuntu.. The only usb device that I works for me is my mouse, and that sometimes gives me trouble.

---

