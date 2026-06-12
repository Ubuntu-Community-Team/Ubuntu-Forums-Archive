---
title: "gcc and repartitioning"
date: 2006-06-18
forum: Desktop Environments
---

### Post by metalsam on 2006-06-18
Two questions:
When I installed I found the partitioning tool awful too use and ended up a bit confused. So I know have a blank partition of 35Gb and a root of 5Gb on my 40Gb HD. Can I merge the two ? How?

Second, ubuntu doesnt have a compiler or rpm support (that ive been able to find). So how can I sinstall gcc so that I can install binaries ?

---

### Post by raptros-v76 on 2006-06-18
ubuntu uses apt (debian package installer)

---

### Post by aysiu on 2006-06-18
If the blank partition is after the root partition, you can merge the two with a live CD and QTParted or GParted.

For GCC stuff, pop in the Ubuntu CD (either Alternate or Desktop) and type ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by metalsam on 2006-06-18
raptros - i tried that, but xchat isnt in the repostitry.
asyiu - that code didnt work for me :S I jsut reinstalled isntead. I still have a Gb i cant access, but im not bothered by it. GParted locked out the partitions i wanted to edit :S

---

