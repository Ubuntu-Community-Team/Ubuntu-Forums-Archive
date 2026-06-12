---
title: "How much free space?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Airjoe on 2006-06-11
How can I tell how much free space I have on a drive?

Thanks

---

### Post by Arnaud_B on 2006-06-11
$df -h
A.

---

### Post by snellgrove on 2006-06-11
If you go to the System menu, Administration, Disks.

Then choose the right disk, and go to the Partitions tab, it'll show you how much free / used is on that partition.

Doesn't really show free space, but a nice way of showing where your space is being used, is to install Filelight.

```
sudo apt-get install filelight
```

---

