---
title: "how to change /media/disk to /media/usbdisk"
date: 2008-01-14
forum: Desktop Environments
---

### Post by unixer on 2008-01-14
Hello,

I use Ubuntu Gutsy Gibbon with Gnome.

When I insert a USB stick it is automatically mounted on /media/disk.  I need to have it mounted as /media/usbdisk.  How can I change this behavior?

As far as I know gnome-volume-manager is responsible to mount it but I can't find a relation to /media/disk.

Thanks in advance for your help,
Bernard

---

### Post by ezramorris on 2008-01-14
> **unixer said:**
> Hello,

I use Ubuntu Gutsy Gibbon with Gnome.

When I insert a USB stick it is automatically mounted on /media/disk.  I need to have it mounted as /media/usbdisk.  How can I change this behavior?

As far as I know gnome-volume-manager is responsible to mount it but I can't find a relation to /media/disk.

Thanks in advance for your help,
Bernard

Hi,
this should work:

-Places > Computer
-Insert USB stick
-When it appears, right click it > Properties
-Volume tab > settings drop down
-In mount point, type the name you want to call it; in this case, type:
```
usbdisk
```
(don't type /media/)
-Close
-Right click > Unmount
-Remove and reinsert, it should now be called usbdisk, and be located at /media/usbdisk.

Hope this helps.

---

### Post by unixer on 2008-01-14
Thanks a lot ezramorris,

That fix it!!!

Bernard

---

### Post by ezramorris on 2008-01-14
> **unixer said:**
> Thanks a lot ezramorris,

That fix it!!!

Bernard

That's OK.

---

