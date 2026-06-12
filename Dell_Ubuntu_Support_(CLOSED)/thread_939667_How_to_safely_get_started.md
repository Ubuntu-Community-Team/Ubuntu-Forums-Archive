---
title: "How to safely get started?"
date: 2008-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mysearch on 2008-10-06
Hi,
Initially, I tried to raise my basic questions in the “*Absolute Beginners*” forum, but the half-life for any thread, before it disappears onto page 2 and beyond, seems to only be a matter of minute! So I thought I would try my luck in this Dell forum, in the hope that my questions will stick around for a few hours, plus the fact that both my systems are Dell laptops (1525, 1300):-({|=

Basically, I just wanted to try Ubuntu for a few weeks booting from a CD to get some feel of the software, applications and issues. So I created a boot CD (8.04.01) via the ISO Recorder and made my laptops dual boot from the CD. Both boot OK, but there is a list of problems with both installations, e.g. no wireless, no sound etc, which I can see dozens of threads repeatedly discussing. 
[I]
Is this really the only starting point? [/I]

While I would plan on eventually partitioning my hard drive for dual boot, (I need to retain Windows in the short term), I simply wanted to try Ubuntu for a few weeks before having to do any major changes to my systems, which are both in daily use. However, the problems associated the standard CD boot, downloaded from the Ubuntu website, effectively prevents me from do this, so my question is:

*Is there any way to put together a boot CD with the necessary driver/firmware fixes that will allow this?*

I see from one thread that Dell now actively support Ubuntu and have an ISO download, which seems to fix many of the issues, but re-partitions the disk by default.
[http://ubuntuforums.org/showthread.php?t=890991&highlight=dell+iso](http://ubuntuforums.org/showthread.php?t=890991&highlight=dell+iso)

Thanks


[I]P.S. A few thoughts and first impressions for what they are worth:

1)	It would seem that Ubuntu aspires to be end-user solution (?), if so, it seems strange that the modification process appears so heavily based on Unix command line syntax. Microsoft learnt this was not the way to go with the end-user market 20 years ago, but then again then they ended up with Vista, so who knows.

2)	Many people, like me, are fed up with Microsoft and rising application costs, especially after Vista, but need some confidence before migrating into the unknown. I not sure many existing Windows users really want to master Unix, as a first step, before they can understand how to get Ubuntu to work on their specific systems, e.g.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

3)	Given the expertise and effort that has undoubtedly gone into Ubuntu, would it not be worth investing some effort into a mechanism that allowed the the boot CD to be customised with the required fixes for a given system prior to download – is Dell active in this area?[/I]

---

### Post by mahdvic on 2008-10-11
Your best bet is to start of with Wubi which is included in 8.04.  Run the CD from inside windows and it will set up the dual boot for you with no problem.  When you are done testing simply uninstall from inside windows like any other application.

---

### Post by aysiu on 2008-10-11
A great place to start would be installing Ubuntu as a virtual machine inside Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Mysearch on 2008-10-12
Thanks for the feedback, much appreciated. However, I have decided to abandon Ubuntu for the time being as explained in the following post: [http://ubuntuforums.org/showthread.php?p=5950824#post5950824](http://ubuntuforums.org/showthread.php?p=5950824#post5950824)

Some quick responses to the comments posted:

> *#2: Your best bet is to start of with Wubi which is included in 8.04. Run the CD from inside windows and it will set up the dual boot for you with no problem. When you are done testing simply uninstall from inside windows like any other application.*

Unfortunately, while I tried this approach, which may be a good starting point for many, some of my hardware wasn’t configured properly, i.e. wireless, sound. As such, this prevented me from using Ubuntu in any serious way.

> *#3: A great place to start would be installing Ubuntu as a virtual machine inside Windows: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)*

I agree. After overcoming Vista’s dire warning about installing Virtualbox, it worked fine, except for the screen resolution problem (800x600). I read and tried lots of fixes after installing the guest additions, but with no luck. To honest, by this time I had been trying to get a working system of Ubuntu for both my Dell 1525 and 1300 for about a week and essentially ran out of time and patience. As such, I have been forced back to work under the dreaded Vista.

However, I will probably get around to trying Ubuntu again in the future, because what I saw looked very good. Thanks

---

### Post by H4ck3rz on 2008-10-16
vmware maywork also you can download & install drive on vmware & it will store it in the image file i use it for backtrack 3 in windows so i guess it will work for ubuntu also

---

