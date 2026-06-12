---
title: "fix partiton"
date: 2009-03-22
forum: General Help
---

### Post by ccdigitalfx on 2009-03-22
I have a desktop with 160 GB of hard drive space, 50% is windows XP and the other was linux. I say was because I had to remove linux, it just wasn't compatible with my SiS video card and was causing all kinds of chaos. I went thru the steps of removing linux as per the internet (deleting linux partitions and repairing the MBR so windows would boot normally) What I need to know is how do I get windows to absorb the unallocated (useless) 50% of my hard drive so I have all my storage back. Any help is greatly appreciated.:)

---

### Post by drs305 on 2009-03-22
I would recommend a windows partitioning program but you could also do it from the ubuntu livecd. Boot to the desktop, then select System, Administration, Partition Editor. You can then delete the linux partition and expand the windows partition to recover the unused space.

Defrag your windows partition at least once prior to starting, and whenever dealing with partitions, backup any critical data before doing any of this.

---

### Post by ccdigitalfx on 2009-03-29
Thanks drs305 I did what you said and it worked!! Thanks for responding so soon! ~C.

---

