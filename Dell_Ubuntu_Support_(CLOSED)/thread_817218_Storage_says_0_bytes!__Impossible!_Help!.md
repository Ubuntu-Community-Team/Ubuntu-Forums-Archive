---
title: "Storage says 0 bytes!  Impossible! Help!"
date: 2008-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HuskySpade on 2008-06-03
Hello,

I was a user of Ubuntu 6.06 and havn't really messed with it in about two years.  However I decided yesterday to upgrade my Ubuntu in an attempt to make my laptop useful again.

Its a Dell Inspiron 4150, with Ubuntu 8.04

This issue is quite strange.  Every time I try to download something from the net, I get errors saying "Insufficient Space" (Default saves to desktop right?)  It worked on the first time I booted the system with 8.04, but awkwardly, all my storage has disappeared since!  I look in the browser and for desktop "0 bytes available" I check File System "0 bytes available".  The only partition that says it has space is my FAT 32 partition which is used for OS Share.

This is impossible!!!  I know I have storage space!!!  This is very frusterating.  It was these kinds of issues that made me veer away from Ubuntu in the first place.  Because it seems as if there is always something wrong, nothing is ever working like it should.  Fix one thing, down goes another.

Please help!  How can I resolve this issue!  I know I have space!  Why can't Linux recognize that?

Thanks in advance!

---

### Post by nick_h on 2008-06-03
Please post the output from:
```
df
```

---

### Post by HuskySpade on 2008-06-03
the code reads as follows

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              7060308   6717296         0 100% /
varrun                  257896       108    257788   1% /var/run
varlock                 257896         0    257896   0% /var/lock
udev                    257896        56    257840   1% /dev
devshm                  257896        12    257884   1% /dev/shm
lrm                     257896     38704    219192  16% /lib/modules/2.6.24-17-386/volatile
/dev/sda4              4681816    369828   4311988   8% /media/hda4
overflow                  1024        20      1004   2% /tmp

```

What I dont understand, is on my first boot, I had tons of space on my Ubuntu partition and any successing boots suddenly it reads full?  

Thanks for your input.

---

### Post by nick_h on 2008-06-03
It looks like your root filesystem is full which will cause you problems.

A good tool to look at usage is Applications->Accessories->Disk Usage Analyser.

---

### Post by rodrigo666 on 2008-06-19
I'm having the same problem, the strange thing is that yesterday I've got tons of free space on my root, and now it's all gone.

What could cause this and how do I can cleanup some space?

Does Ubuntu have some assistant to do this like Windows? Some CCleaner could come handy.

---

