---
title: "Conky Config Help"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by rogers45 on 2007-11-23
Hello, I am need some help whit my Conky Config,

Right now it is show

/ 13.24GiB / 36.17GiB

usr 13.24GiB / 36.17GiB

boot 13.24GiB / 36.17GiB

home 13.24GiB / 36.17GiB

tmp 13.24GiB / 36.17GiB

All have the same info? How to fix this?

Regards rogers

---

### Post by Gambini on 2007-11-23
It looks like you only made one partition for your Ubuntu installation. To make those read correctly, you would need to boot on to the install disk and change the partitions. You would more than likely lose all of your data, so back it up if you can.

Make a partition for each of those, or just for "/" and "home" (as I did). This will make upgrading your install much easier, because you will only need to format the root partition and save all the data on the home partition. Alternatively, you could delete all of the stuff in the conky config file about the drives, and just leave one of them. That would make it look a little more clean, rather than displaying the same information 4 times.

Take all that in context that I am a recent Linux non-noob. If someone wants to verify what I just said,  or say it in a more comprehensive way, please do.

---

### Post by rogers45 on 2007-11-24
> **Gambini said:**
> It looks like you only made one partition for your Ubuntu installation. To make those read correctly, you would need to boot on to the install disk and change the partitions. You would more than likely lose all of your data, so back it up if you can.

Make a partition for each of those, or just for "/" and "home" (as I did). This will make upgrading your install much easier, because you will only need to format the root partition and save all the data on the home partition. Alternatively, you could delete all of the stuff in the conky config file about the drives, and just leave one of them. That would make it look a little more clean, rather than displaying the same information 4 times.

Take all that in context that I am a recent Linux non-noob. If someone wants to verify what I just said,  or say it in a more comprehensive way, please do.

Hmm okay, Thank you, but i keep only "/" in conky,

---

