---
title: "In the event of HD failure..."
date: 2009-06-17
forum: General Help
---

### Post by mesmith on 2009-06-17
I'm new to Linux, and trying to develop a strategy to recover from HD failure if it occurs. I have two HD's. On my primary HD I have two partitions, Linux and Swap. My backup HD is a single partition. I have captured and saved the primary drive's MBR to my backup HD, along with an image of my primary Linux partition (using partimage).

In the event of primary HD failure, I would install, partition and format a new HD using RescueCD (two partitions, Linux and Swap). This disk would likely be larger than my old disk. I would restore the MBR, then restore the Linux image.

Would this procedure work, or would all hell break loose?

---

### Post by iponeverything on 2009-06-17
It should be easy enough to test with a non-production machine.

But it does sound like it should work fine.

---

### Post by tgalati4 on 2009-06-17
sudo cp /dev/sda /dev/sdb

If both drives are similar size, this is a quick way to clone a drive.

Better strategy--just back up your home directory and use  a live cd for emergency boot.

---

