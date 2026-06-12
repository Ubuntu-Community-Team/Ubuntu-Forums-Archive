---
title: "[SOLVED] How many slices?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by saul_2110 on 2006-07-21
How many partitions I should have within the same HDD? I mean, is there a  number of partitions after which, the throughput starts decreasing?

---

### Post by simonn on 2006-07-21
> **saul_2110 said:**
> How many partitions I should have within the same HDD?

As many as you need :).

Seriously though, I would suggest at least 3; /, /home and swap.

> I mean, is there a  number of partitions after which, the throughput starts decreasing?

I do not think performance is a problem.

The only limitation I can think of is that there is a maximum of 4 primary partitions. So if you want more than 4 partitions you must make one of the primary partititions an extended partition and create the rest of the partitions inside of it.

---

### Post by hw-tph on 2006-07-21
> **saul_2110 said:**
> How many partitions I should have within the same HDD? I mean, is there a  number of partitions after which, the throughput starts decreasing?

Performance may suffer if you move a lot of files between different partitions. Moving withing the same partition is near-instantaneous but moving across two partitions means copying and deleting the actual files. This can take some time if the files are numerous or very large. Usually this is not much of a problem since it is a thing you don't do very often, but it all depends on your usage of course.


Håkan

---

