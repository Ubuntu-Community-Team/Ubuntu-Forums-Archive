---
title: "can u defragment a linux partition?"
date: 2009-03-05
forum: General Help
---

### Post by vistadude on 2009-03-05
now i no that the ext3 file system is made so that it won't get fragmented, how ever i have heard some people saying that it will actually get fragmented a bit, but defiantly not as much as an ntfs partition. And so to day from within my windows 7 partition i decided to defragment my windows partition, and the linux diver showed up, so what i did was I analogized it, and it showed up as 6% fragmented. Should i defragment the ext3 file system? or is this showing up as fragmented because windows can not properly read a ext3 file system. What do u think? and if it is because of that, then how would i be able to defragment the ext3 file system, because as i said before, in same cases even the file systems that are not meant to get fragmented some times will to a certain degree

---

### Post by 73ckn797 on 2009-03-05
I would not worry unless the partition is nearly full. I read somewhere that Ubuntu can frag some due to limited disk space. I could be wrong. I do not know whether trusting the MS analysis would be good for a Linux drive.

---

### Post by damis648 on 2009-03-05
I would not trust any operating system that does not have native support for Ext3, you have no idea if those 3rd-party drivers might end screwing stuff up. Try [this]("http://ubuntuforums.org/showthread.php?t=169551") defrag tool.:popcorn:

---

### Post by bodhi.zazen on 2009-03-05
There are several issues that come up.

First, every file system will have some fragmentation, it is just that linux native file systems are less prone to fragmentation then FAT or NTFS.

This is the "classic" link :

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

The fragmentation on ext3, for example, very rarely affects performance.

Ext4 is available in 9.04 alpha and rumor is Fedora 11 it will be default. ext4 has a number of interesting features, including a defragmentation tool.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by vistadude on 2009-03-05
> Ext4 is available in 9.04 alpha and rumor is Fedora 11 it will be default. ext4 has a number of interesting features, including a defragmentation tool.


ya, i was looking into ext4 a bit, but they were saying it is likely going to have some bugs for now until they start using it more, but with what ur saying, dose that mean that it is more likely to get fragmented than an ext3 file system, or just about the same, but they made it so that u can still defrag to get that bit that is fragmented

---

### Post by dcstar on 2009-03-05
> **bodhi.zazen said:**
> There are several issues that come up.
........
The fragmentation on ext3, for example, very rarely affects performance.
........

The bottom-line on this issue **is** performance, and the reality is that unless you let your Linux filesystem get over ~90% full then any fragmentation is kept under control and there is no performance degradation in "real life" use.

The experience with Windows is (still) gradual deterioration in performance over time as fragmentation increases. Since Linux does not suffer in this way then the thinking of people that "I need to defragment" does not apply.

DOS/Windows has spawned so many money-making enterprises over time to alleviate its inherent limitations, I love to know how much money has been made from the various Disk Maintenance/Anti Virus/Security products that people have found "necessary"......   :-(

---

### Post by Afkpuz on 2009-03-05
I don't know the specifics, but I heard that linux defrags automatically on the fly.

---

### Post by bodhi.zazen on 2009-03-05
> **vistadude said:**
> ya, i was looking into ext4 a bit, but they were saying it is likely going to have some bugs for now until they start using it more, but with what ur saying, dose that mean that it is more likely to get fragmented than an ext3 file system, or just about the same, but they made it so that u can still defrag to get that bit that is fragmented

ext4 is now considered stable.

That is not the same as bug free mind you , but personally I use ext4 in a VM with no problems not have I heard of any problems with ext4.

---

