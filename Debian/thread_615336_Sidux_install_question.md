---
title: "Sidux install question"
date: 2007-11-17
forum: Debian
---

### Post by 67GTA on 2007-11-17
I was looking at the Sidux installer (live cd). I was a little nervous about the partitioning tab. I have Ubuntu on sda1. I created sda2 for Sidux. I set sda2 as root. The bottom of the page says "set mount points of other partitions". If I leave sda1 checked, but leave the mount point blank, will it automatically mount it at boot and not format it?

---

### Post by LaRoza on 2007-11-17
Setting mount points of existing partitions doesn't format them. It only has them mounted at start up. 

I personally don't mount a partition if another OS is installed on it.

---

