---
title: "Help: bootloader onto sda or sda1 .. trying to install ubuntu on a usb stick"
date: 2009-01-23
forum: General Help
---

### Post by bosworthy on 2009-01-23
Hi,

I have two questions:

1)
According to [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)

the tutorial recommended the installation of the boot loader to /dev/sda instead of /dev/sda1.  I realize the tutorial did an install on the full usb stick.  For me, I've partitioned my usb stick in two:

/dev/sda1  for ext3
/dev/sda2  for ntfs.

In my case, should the boot loader be installed to /dev/sda or /dev/sda1?

2)
After the installation has finished, how do I set the temp directories to point to the ramdrive?  I haven't install any ramdrive utility yet, but I hear installing a ramdrive type software will prolong the life of my usb stick.


Thank you.

---

### Post by bosworthy on 2009-02-02
bump.

does it matter, sda or sda1?  I've installed it on sda and it works, but I'm now asking from a theoretical perspective.  I currently want to backup my mbr, but i'm not sure if i should use sda or sda1  ..does it make any difference in my case since sda1 comes before sda2.

thanks.

---

