---
title: "copy ubuntu cd ??"
date: 2005-11-14
forum: Desktop Environments
---

### Post by trufflesdad on 2005-11-14
On copying my ubuntu cd to give to friends I get the following output...

wager@whitebox:~$ sudo dd if=/dev/hdd of=kubuntu.iso
Password:
dd: reading `/dev/hdd': Input/output error
1311680+0 records in
1311680+0 records out
671580160 bytes transferred in 257.631742 seconds (2606745 bytes/sec)
twager@whitebox:~$

The cd I burn boots up ok and I have tried it up the the partition level so I assume it should install but before I pass it out and burn some more can
anyone advise me about the input/output error ??

---

### Post by reedlaw on 2005-11-14
I don't know about your error, but I have always found K3b to work without a problem.  It also checks md5sums automatically so you can compare with the official ISO.

---

