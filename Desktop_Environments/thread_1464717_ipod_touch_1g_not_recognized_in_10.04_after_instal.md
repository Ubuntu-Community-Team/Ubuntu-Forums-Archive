---
title: "ipod touch 1g not recognized in 10.04 after installing ifuse"
date: 2010-04-28
forum: Desktop Environments
---

### Post by khughitt on 2010-04-28
Has anyone had any luck?

I'm using a fresh install of Kubuntu 10.04. I tried to add support for syncing iPod touch with Amarok 2.3.0 following a recently posted guide ([http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html](http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html)), but even after rebooting, I cannot get the iPod to mount.

The system definitely detects it:

```

$ lsusb
Bus 001 Device 007: ID 05ac:1291 Apple, Inc. iPod Touch 1.Gen

```

But it is not automatically mounted when I plug in the device, and manually attempting to mount the iPod results in:

```

ifuse /media/ipod/
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

```

The iPod is using firmware 3.1.3.

Any ideas?

---

### Post by deadbinky on 2010-07-09
I am having this exact same problem - did you ever get it fixed?

---

