---
title: "Support time of Xubuntu and its community packages"
date: 2012-02-20
forum: Desktop Environments
---

### Post by stfischr on 2012-02-20
Hi.
 
 Xubuntu will become LTS in 12.04 and be supported 3 years. But where can  i see witch packages are in this 3 year support time? Only the  preinstalled ones or are packages like xfce4-goodies also 3 years  supported?
 
 How can I find out how long package X is supported. apt-get support-time  would be nice, :) but I don't think its in the package database. Is  there a list somwhere in the internet?

Greetings, stfischr

---

### Post by Lisiano on 2012-02-20
The 3 year support is for everything in the ubuntu repositories for 12.04 as long as it is in the official repositories (Be it main, extra, universe or multiverse) then it should be supported. PPA support is decided by the PPA maintainer.

---

### Post by stfischr on 2012-03-08
Oh, I totaly forgot this thread. Thanks for your answer.

I always thought universe and multiverse are maintained by the community and there is no guarantee vor 3 years support/updates?

Now I'm more confused than before. :)

---

### Post by mikodo on 2012-03-08
I would like to know this too! 

I remember a discussion I had with Mterry, the developer of Deja-dup. He ran into a couple of problems, with the Lucid packages.

It was breaking for a couple of reasons:

1. Duplicity had not corrected then, (supposedly now) a bug that found it's way into Deja-dup and effected its' performance, with Lucid and wouldn't work. Eventually, it was fixed, and was ported to Lucid's Deja-dup's version. So, in this instance, because Mterry and other devs of duplicity, got on to fixing, the upstream bug, it was fixed for Deja-dup. But, what if other maintainers of other apps/packages, didn't fix bugs for such an old release as Lucid? Then, it would indicate that packages in LTS releases are supported only, as long as the devs, are able to maintain the packages.

2. Slightly different issue, but similar -> Anyone, using Lucid, cannot use a PPA of Deja-dup, or compile the newer packages of Deja-dup, because the code-base is different for Lucid, than in more recent releases. With Lucid,  one must remain with the older versions, even if they wanted to upgrade packages for it. Too me, that is a bug.  

So, I think, the answer is that one cannot expect the packages, that outside maintainers are maintaining, to always be supported, for the 3 LTS cycle ... which is a shame.

Hope this helps.

Here is a bug, about the second point:  

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/578045](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/578045)

---

### Post by Peripheral Visionary on 2012-03-09
Am I correct in assuming that the stuff in the Ubuntu repositories will be [supported for **5 years**]("https://wiki.ubuntu.com/LTS") rather than 3 this time even though Xubuntu itself is only supported for 3?

 > In previous releases, a Long Term Support (LTS) version had 3 years  support on Ubuntu (Desktop) and 5 years on Ubuntu Server. Starting with  Ubuntu 12.04 LTS, **both** versions will receive 5 years support.  from the Ubuntu Wiki

Thanks! How does that work anyway - that Ubu gets 5 years and Xubu gets 3? Seems to me that at least the Ubu part of Xubu will be supported for the full 5 years.

---

