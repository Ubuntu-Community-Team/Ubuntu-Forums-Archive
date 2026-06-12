---
title: "Can't re-partition Dell 2TB disks"
date: 2012-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ltenny on 2012-01-03
OK, this one I can't figure out. I've built a small cluster for Apache Hadoop using 10 Dell R415's each with 4 2TB disks. Each configured JBOD (no RAID). I'm running Ubuntu 11.04. I configured and installed everything a few months ago and everything was running great. Then the Hadoop hdfs disks on 4 of the servers got corrupted (I shut things down poorly, my bad). Anyway, I had all the data backed up, so I figured I would just re-partition and re-create the file systems on the 4 servers I skrewed up and re-load. Unfortunately, I can't get that to work. I partition with fdisk (also tried parted) and then create the file systems with mkfs.ext3 just like I did when I created the cluster, but when I join the machines to the hdfs cluster, the disks quickly fail. It's so bad, the ls command spits out a bunch of ????? marks and reports I/O errors. If this were just one disk, I think it's hardware. It happens on 3 disks in each of the 4 machines (one disk on each machine is used for the OS, not data and didn't get corrupted). The crazy thing is if I swap out the disks with brand new, strait-from-the-factory disks I can fdisk and mkfs.ext3 and they work great. So, the bottom line is these disks can only be partitioned once! Really? I figured fdisk or mkfs was overwriting some bad block table from the factory. I ran badblock (runs forever) but it can't find any bad blocks. I posted to the Apache Hadoop forums and no one has ever heard of this. So I'm turning to the experts. 
 
-larry

---

