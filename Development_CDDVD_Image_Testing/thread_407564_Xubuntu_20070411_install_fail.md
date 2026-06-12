---
title: "Xubuntu 20070411 install fail"
date: 2007-04-12
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-04-12
20070411 Xubuntu install trial on a 4 boot system, 2 IDE hard drives:  Win 98 hda1 & Ubuntu Dapper hda2, Ubuntu Edgy hdb1 and Ubuntu Feisty hdb3.

Install trial of Xubuntu Feisty on hdb1 partition got:

"The ext3 file system creation IDE1 slave hdb failed". 

I had installed Xubuntu 20070402 on another hard drive O.K. so I was a bit surprised.

So I installed Xubuntu Edgy on hdb1 just fine, same partition that "creation failed", which is what I'm entering this post from.

Let me go see if Ubuntu Feisty hdb3 still boots and if so resync Xubuntu.

Cheers, Jerry :confused:

---

### Post by j1mc on 2007-04-13
> **jerrylamos said:**
> 20070411 Xubuntu install trial on a 4 boot system, 2 IDE hard drives:  Win 98 hda1 & Ubuntu Dapper hda2, Ubuntu Edgy hdb1 and Ubuntu Feisty hdb3.
{snip}
Cheers, Jerry :confused:

Hi Jerry, if you are going to do testing of xubuntu ISO's, please do so through the ISO testing process.  I've sent out a few emails to the xubuntu-devel and xubuntu-user mailing lists concerning this, so the instructions on what to do are easily accessible.  Also, reporting your test results through the appropriate channels will help the developers to better collect the test successes and failures, and helps to make xubuntu better.  Thanks for your help.

---

### Post by jerrylamos on 2007-04-13
This forum is titled "CD/DVD Image Testing" which is why I posted to it.  I am registered for testing and I have tried some links as mentioned in the previous post.  One didn't seem to be active.  On another I got an authentication alert from the browser.  Lately they seem to be inactive because of some build problems.  I presume when they get daily builds going again the links will get sorted out.

When I get a situation I can identify as a bug it goes on Launchpad.  Sometimes of course I could be having a hardware problem; I don't know yet whether this thread is my hardware problem or a "CD/DVD Image" problem.  One of the things we use the forums for is to see if other people are having a similar problem, or if there is a workaround, or whatever.

Anyway, there's a broadcast note: "The Ubuntu 7.04 release candidate (due today) has been delayed" so I'm waiting for the next build to see if the problem that started this thread is still around.  At the moment I'm inclined to think it was/is software because both hard drives I got the ext3 format failure with now have other Ubuntu's installed and running.

Cheers, Jerry :neutral:

---

### Post by jerrylamos on 2007-04-15
My 20070414 install problems are entered in the isotesting results:
1. Manual partitioning didn't work for deleting, new, and resizing an existing partition bug #99908.
    Edit to remount as / and re-format did work.  I'm entering this from that install now.
2. Xubuntu won't boot on a 1 gHz Celeron 384 mb Intel 845G type graphics because "can't access tty" bug # 99757.  This hardware runs Dapper, Edgy, Knoppix, ... very nice, crisp, and quick with a 17" 1280x960 LCD screen.

Net: if Feisty doesn't work, there's always Dapper.....

Cheers, Jerry :confused:

---

### Post by michwill on 2007-04-22
I'm not tester per se, but I'm having trouble installing Xubuntu as well.  Neither manual nor Guided partitioning works.  It always fails with the "ext3 file system" couldn't be created error.  Any insights as to what is occuring would be most appreciated.

Thanks,
Michael

---

### Post by jerrylamos on 2007-04-22
Michael, there's some more detail in [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259)
including a workaround.

Another workaround is to use the standalone partitioner downloaded from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) which I've found better than the built-in partitioners, granted they are all dangerous.

What I did since there was a suitable existing partition was to edit the partition to change the mount point to / and then checked format.  That all worked.  If you'd like to juggle partitions then try gparted downloaded from the link.  I think there's a package gparted that you could access from Applications, Add/Remove to install on CD Live if you don't want to download and burn the standalone gparted.

Cheers, Jerry

---

