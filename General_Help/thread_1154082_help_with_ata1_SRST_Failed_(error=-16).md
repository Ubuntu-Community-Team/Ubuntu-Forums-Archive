---
title: "help with ata1: SRST Failed (error=-16)"
date: 2009-05-09
forum: General Help
---

### Post by ihaveabu on 2009-05-09
i get these 2 messages after grub loads:
11.752017 ata1: SRST Failed (error=-16)
21.764016 ata1: SRST Failed (error=-16)

i don't have dual boot. i only have ubuntu installed on my hdd with 1 partition.

my computer specs are:
P4 2.4C northbridge
Asus P4P800 pro or w/e it's called
2GB DDR2 PC3200 ram
Ati Radeon 9600
120 GB HDD (i think it's a seagate or WD, forgot)
2 DVD-RW drives

all my devices are hooked up via ATA, no SATA

what up with the error messages?

---

### Post by Triptol on 2009-05-09
There used to be a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706). One guy fixed it by setting his drive to cable select, I don't know if that will work for you.

It might be that your disk is broken, or you recently upgraded to a new kernel, that doesn't like your disk.

You might want to check the options offered in this thread:[http://ubuntuforums.org/showthread.php?t=762870](http://ubuntuforums.org/showthread.php?t=762870).

---

### Post by ihaveabu on 2009-05-09
hmm interesting. the disk is definitely not broken.

---

### Post by Triptol on 2009-05-10
Did you try some of the infos in the threads?

Did you get any results?

---

