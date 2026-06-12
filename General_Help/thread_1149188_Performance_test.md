---
title: "Performance test"
date: 2009-05-05
forum: General Help
---

### Post by Frankccngai on 2009-05-05
Hi,

I want to do a read/write performance test on USB mass storage device. And i find that there are 2 common methods for measuring reading speed. But i don't know what is the different between them. Could anyone answer me? Thanks!

The 2 common methods are:
1. hdparm –t /dev/sda1
2. time dd of=/dev/zero if=/mnt/usbdisk/dummy.txt bs =1M count = 10
(some ppl also suggest measuring by script "time cp", i think it is similiar to the 2nd method)


Thanks,
Frank

---

