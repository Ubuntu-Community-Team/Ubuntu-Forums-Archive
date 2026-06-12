---
title: "can I increase my filesystem size"
date: 2012-02-18
forum: Desktop Environments
---

### Post by forsubhi on 2012-02-18
I installed ubuntu on 20 gb extn4 file system and I want to increase the space prepared for ubuntu to 50 gb is there program to do this without burning program to cd and boot from if , I mean program like minitools which works on windows

---

### Post by Paddy Landau on 2012-02-19
Assuming your hard drive has space, this can be done, but you have to boot from a Live CD.

You will need to understand about partitions -- Google it (Wikipedia is a good place).

Boot from a Live CD and use GParted to resize your partitions.

**Warning 1:** Depending exactly how you are resizing, it can take a long time, so be prepared to wait while GParted does its work.

**Warning 2:** Even though this is a truly tried-and-tested method, there is always a small chance of data loss when manipulating partitions, so please **back up your data first**.

---

