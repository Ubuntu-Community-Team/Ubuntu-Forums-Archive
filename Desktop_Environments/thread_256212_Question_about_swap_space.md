---
title: "Question about swap space"
date: 2006-09-12
forum: Desktop Environments
---

### Post by alecjw on 2006-09-12
How does Linux use swap space? (i know it's RAM pon the HDD) Does it only use the swap space on the hard drive from which Ubuntu is booted? Can it only use 1 swap partition? CAn you have one hard disk for data and another for swap? Can you have swap on a pen drive so that you can just plug it in when you're doing video editing or something memory intensive then unplug it? Can you run an entire system solesly off of sawp with no physical RAM at all or does the BIOS need it?
Just curious...
Thanks

---

### Post by lagagnon on 2006-09-13
> **alecjw said:**
> How does Linux use swap space? (i know it's RAM pon the HDD) Does it only use the swap space on the hard drive from which Ubuntu is booted?

That is the default location for the swap partition created
>  Can it only use 1 swap partition?
No.
>  CAn you have one hard disk for data and another for swap?
Yes.
>  Can you have swap on a pen drive so that you can just plug it in when you're doing video editing or something memory intensive then unplug it?
Yes, but you will have to turn the swap on and off.
>  Can you run an entire system solesly off of sawp with no physical RAM at all or does the BIOS need it? I doubt it but maybe. I have no idea why you would want to do that as your system would be VERY VERY SLOW.

Suggest you read:
[http://www.lissot.net/partition/partition-04.html](http://www.lissot.net/partition/partition-04.html)
[http://www.faqs.org/docs/Linux-mini/Partition.html#SWAP-PARTITIONS](http://www.faqs.org/docs/Linux-mini/Partition.html#SWAP-PARTITIONS)
man mkswap
man swapon

---

### Post by anaconda on 2006-09-13
> CAn you have one hard disk for data and another for swap?
yes you can, but how much swap are you goin to meake? a whole hard-disk! huh..

> Can you have swap on a pen drive so that you can just plug it in when you're doing video editing or something memory intensive then unplug it?
In theory you can, but it would be pointless. because a pen drive is much slower than a hard-disk, and more importantly pen-drive actually wears out if it is constantly written to. (Was it on average 100000 writes to usb-stick before it wears out??)

If you want to have different sizes of swap at different times, then you could make swap files to your hard-disk when needed.

---

