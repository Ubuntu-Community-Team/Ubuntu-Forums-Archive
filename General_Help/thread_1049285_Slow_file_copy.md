---
title: "Slow file copy"
date: 2009-01-24
forum: General Help
---

### Post by davidself1001 on 2009-01-24
When I copy a large file my copy speed is only 20MB/s.  That seems very low.  I have tweeked some vm params in systl.conf (ie vm.vfs_cache_pressure=50 and vm.swappiness=1).  Could that be the reason for copies being so slow?

---

### Post by Hooya on 2009-01-24
Where are you copying to where else?  Are you copying across partitions, within the same partition, across different drives?  What kind of drives?

20MB/s doesn't seem too slow if you're copying a file from one part of a physical disk to another part of a physical disk, depending on your drive of course.

---

### Post by gjoellee on 2009-01-24
If you are copying to an external drive, this can be considered normal. However if it is on the same partition on the same HDD 20mb/s is slow (however it depends on your hardware).

Trying an other file browser can help a lot. I use "PCManFm" which has a lot of options and is super fast and super lightweight. Try it: ```
sudo apt-get install pcmanfm
```

---

### Post by davidself1001 on 2009-01-24
That speed was copying within the same partition.

---

