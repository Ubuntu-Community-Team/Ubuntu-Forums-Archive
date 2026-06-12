---
title: "How to increase size of a home directory?"
date: 2010-02-22
forum: Desktop Environments
---

### Post by vksingh on 2010-02-22
Hi,

I am using ubuntu 9.04 from past 6 months. The size of my home directory was default. I want to increase the size of my home directory. How can I do it?


Thanks,

Vivek

---

### Post by mcduck on 2010-02-22
There is no size limit on any directory (unless you have enabled quotas and defined such limit yourself, in wich case you'd surely know how to change the limit as well).

The available space in your /home is limited only by the available space on the hard disk partition where your /home is located.

---

### Post by Hero of Time on 2010-02-22
And if you happen to have /home on a separate partition than /, you need to resize the partitions. To do that, use GParted from a live CD, check the UUID strings after the resize and and compare them to your own fstab entry, update as needed. You have to mount your / file system before you can edit it's fstab.

---

