---
title: "Extremely Slow Boot Time"
date: 2009-01-16
forum: General Help
---

### Post by falconed7 on 2009-01-16
Hey everyone!

I am experiencing extremely slow boot times with Ubuntu 8.10 when dual booting with Vista on my laptop. 

I installed bootchart and have the following image:

---

### Post by linuxisevolution on 2009-01-16
> **falconed7 said:**
> Hey everyone!

I am experiencing extremely slow boot times with Ubuntu 8.10 when dual booting with Vista on my laptop. 

I installed bootchart and have the following image:

It seems that **hald**, **readahead-list**, and **fsck** are making your boot time long. Look up on each one to disable each. You might be doing a disk check every boot, look and see. I can't tell much else from that image, good program though. :)

---

### Post by falconed7 on 2009-01-17
> **linuxisevolution said:**
> It seems that **hald**, **readahead-list**, and **fsck** are making your boot time long. Look up on each one to disable each. You might be doing a disk check every boot, look and see. I can't tell much else from that image, good program though. :)

Okay thanks, I'll check them out.

---

