---
title: "put in new drive, busybox at boot"
date: 2009-01-02
forum: General Help
---

### Post by seks2 on 2009-01-02
Sorry for so many threads today, I'm having a lot of problems :-#

When I plugged a new HDD into the 1st sata port (and moved the original boot drive into the 2nd), the ubuntu install on it got stuck at a busybox. I think it couldn't find the kernel based on the uuid or something.

What's a quick fix for this? :popcorn:

---

### Post by x22 on 2009-01-02
assuming your /boot directory is on the original drive, that
*was* /dev/sda, now the new one is /dev/sda and the original is
/dev/sdb.  So you have to tell the bootloader about this: wherever
the configuration file says "/dev/sda" change it to "dev/sdb"--
likely you'll need a live-CD distro such as knoppix or systemrescue
to do this.

---

### Post by seks2 on 2009-01-02
I got the same "gave up waiting for root device" when I did that, but instead of saying "/dev/by-uuid/### does not exist" it says "/dev/sdb3 does not exist". I also tried sda/sda1/sda2/sda3/sdb2/hda :/

---

