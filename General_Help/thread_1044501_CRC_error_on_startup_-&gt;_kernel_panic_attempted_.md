---
title: "CRC error on startup -&gt; kernel panic attempted to kill init"
date: 2009-01-19
forum: General Help
---

### Post by rudd2 on 2009-01-19
I've done some searches and haven't found a solution to my problem

[http://ubuntuforums.org/showthread.php?t=991372](http://ubuntuforums.org/showthread.php?t=991372) - this sounds like a similar problem.

computer is:
intel core2quad Q6600
2GB DDR2 ram (2*1GB)
1x wd 150GB raptor (this drive has windows server 2008 and ubuntu installed)
1x 1TB spinpoint F1 (this drive is for documents only, do not tell me to install an OS on it)
gigabyte p35c dsr3 mobo

problem:
when starting ubuntu (8.10, kenral image is whichever the auto updater last pushed) I intermittently get a kernel panic attempted to kill init message, sometimes it's just a crc error message, aprox a tenth of start up attempts *are successful*.

Aparrently the lines above the panic line are useful in diagnosing the problem, so i've taken some pictures of the error messages.

The most frequent failure message is the kernel panic message:
[http://img50.imageshack.us/img50/1062/p0801090804pw5.jpg](http://img50.imageshack.us/img50/1062/p0801090804pw5.jpg)
occasionally I get the CRC error:
[http://img134.imageshack.us/img134/55/p0801090852mf9.jpg](http://img134.imageshack.us/img134/55/p0801090852mf9.jpg)
today I got this version of the error for the first time:
[http://img48.imageshack.us/img48/7862/p190109093102ch6.jpg](http://img48.imageshack.us/img48/7862/p190109093102ch6.jpg)

The disc used to install ubuntu reported no erros with self check, niether did the previous disc i used before re-instlaling (both produced versions of ubuntu with the same problem, this disc I used to install ubuntu on a different computer which hasn't had the same problem)

I've done several re-installs of ubuntu (and windows - I wiped the whole disc and started from scratch), I've tried preprepating the partitions for windows and ubuntu as well as instlling windows on the wohle drive and using the ubuntu installer to re-size the windows partition.

All install attempts resulted in the same problem.

I've tried forcing a fsck on startup (using the method which involves making a empty file)

I've tried running fsck on the disc from the ubuntu (live) install CD, but it simply prints out some numbers (build date perhaps) and doesn't do anything useful.

Any input on how to fix it would be appreciated.

---

### Post by dcstar on 2009-01-20
> **rudd2 said:**
> I've done some searches and haven't found a solution to my problem
.........
problem:
when starting ubuntu (8.10, kenral image is whichever the auto updater last pushed) I intermittently get a kernel panic attempted to kill init message, sometimes it's just a crc error message, aprox a tenth of start up attempts *are successful*.
..........
Any input on how to fix it would be appreciated.

See if your BIOS has a hard disk delay setting anywhere, it may help if you add in a few seconds to allow the disk to settle before Linux tries to access it.

---

