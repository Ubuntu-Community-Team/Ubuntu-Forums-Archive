---
title: "Grub Loading, please wait Error 21"
date: 2008-01-19
forum: Dell  Ubuntu Support
---

### Post by russ1960 on 2008-01-19
I have an older Dell - Optiplex 160l - with a 2.0 Intel Celeron and a Nvidia 256mb video card.  I have 2 hard drives - split into 4 partitions.

I installed Ubuntu to use as a dual boot on a partion on my back drive.  Everything installed correctly but when I went to reboot I got the following error and the system hangs there.

Grub Loading, please wait Error 21

How do I get by this?  I am a newbie to the inner working of linux.

Thanks

Russ

---

### Post by natehall on 2008-01-19
error 21 means that grub is looking for the grub configuration file on a disk that does not exist. Take a look at /boot/grub/menu1st and see which disk the kernel and initrd parameters point to. They should point to the same disk where /boot is located.

---

