---
title: "Upgrading a Kernel"
date: 2005-09-29
forum: Desktop Environments
---

### Post by seaeric on 2005-09-29
One thing I haven't tinkered with is upgrading my kernel with added modules.  I have an IDE chipset that appears to not full work with Ubuntu and doesn't allow me to enable DMA.  Here is the IDE information and the message I get.


sudo hdparm -d1 /dev/hdc

/dev/hdc:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma    =  0 (off)

0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)

Although, building custom kernels or modifying them is not something I want to do, I should know something about it so any beginner links would be helpful!

Thanks,
Eric

---

### Post by John.Michael.Kane on 2005-09-29
[http://www.ubuntuforums.org/forumdisplay.php?f=58](http://www.ubuntuforums.org/forumdisplay.php?f=58)

[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)
[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

Hope it helps...

---

