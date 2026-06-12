---
title: "mounting kingston usb"
date: 2009-04-06
forum: General Help
---

### Post by saskatchewan on 2009-04-06
ASUS eee 1000 with eee ubuntu 8.04 and Kingston 8 Gig USB

Ok, the only way that I have been able to mount my USB is by typing sudo mount -t vfat /dev/sdc1 /media/USB in a terminal.  However, that only allows me to copy things from that USB.

I want to be able to remove things from the USB and back things up to that USB.

But, the OS does not allow me such permissions.

I have tried finding diskmanager in the synaptic but had no luck.

Can any tell me how I can more easily access the USB and how I can get permissions to use it the way I described.

Thanks

---

### Post by taurus on 2009-04-06
```
sudo umount /dev/sdc1
sudo mount -t vfat /dev/sdc1 /media/USB -o umask=000
```

---

