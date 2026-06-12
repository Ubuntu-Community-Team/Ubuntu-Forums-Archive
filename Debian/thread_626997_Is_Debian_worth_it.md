---
title: "Is Debian worth it?"
date: 2007-11-29
forum: Debian
---

### Post by Fixman on 2007-11-29
I was thinking on switching to Debian, but I had two different sides:

**switch:** Debian is far better than Ubuntu, and Ubuntu is actually based on Debian so you won't notice a big difference

**Don't switch:** Debian packages are outdated, and some scripts won' work!

So, what side are you? Should I change or not?

---

### Post by wjp.reg on 2007-11-29
I found debian "quirkier" to setup; things like getting nvidia driver, samba printing, and sound required a lot more trips to the forum for help, whereas these issues were virtually non-existent in ubuntu.

As far as debian packages go, it depends which stream you want to take; stable, testing, experimental, or roll your own.  In other words, your packages can be as up-to-date as you wish :-)

I run debian 4.x on my work desktop and ubuntu on my lappy.

---

### Post by D-EJ915 on 2007-11-29
actually Debian (not stable) has more updated packages than Ubuntu does.

---

### Post by SunnyRabbiera on 2007-11-29
Yeh, the sid repository is pretty massive, so is the testing...

---

### Post by corstar on 2007-11-30
And you don't get ANY of those nasty X crashes after updates.
That's what drove me away from ubuntu in the first place. I found it so annoying that they didn't test the updates before releasing to the masses and then having to browse with elinks just to find out what to fix..

I have kept Debian Lenny running for 6 months now and love it. 

I reacon  they have the best release policy too... "Release when it's ready".

---

### Post by tommcd on 2007-11-30
I have installed debian on 3 different desktops, plus a laptop. On every system there was no question that debian ran much lighter, faster, and used fewer resources than ubuntu. I did a full install from the 1st debian CD. I did not try to get a lean and mean debian system with just a net-install. If you upgrade to debian lenny/testing your system will be at least as up to date (if not more) as ubuntu. I used debian-testing for about 6 months. Testing gets lots of updates. There are some almost every day. Yet debian remained rock solid stable. This includes kernel updates, xorg updates, libc6 updates gnome updates, you name it.
First install debian etch, then upgrade to testing/lenny by changing your sources.list as per Rickh's excellent tutorial:
[http://forums.debian.net/viewtopic.php?t=13362](http://forums.debian.net/viewtopic.php?t=13362)
One caveat: do not mix testing and unstable or experimental unless you really know what you are doing. As long as you stick with just testing/lenny you will be fine.
One more caveat: ther seems to be some debate on the debian forums about the best way to update your system:
1. apt-get update && apt-get upgrade
2. apt-get update && apt-get dist-upgrade
3. aptitude update && aptitude upgrade
4  aptitude update && aptitude dist-upgrade
You will find seasoned debian users that swear allegiance to apt-get, some to aptitude, some to upgrade, and yet some to dist-upgrade. Very confusing for the novice!
I always did apt-get update, followed by apt-get dist-upgrade. Everything went well. If you use apt-get than stick to it. Same for aptitude.

---

### Post by smartboyathome on 2007-11-30
I'll have to be the first one to say no because, while I like it, it just doesn't cut it with my wireless card and I don't want to connect to ethernet just to get it.

---

### Post by mojoman on 2007-11-30
Go for it. Lenny is both more up-to-date and more stable than Gutsy. The extra work needed for setting things up and configuring it is worth it.

/mojoman

---

### Post by georges023 on 2007-12-02
Didn't vote.
Why?
Cause it depends on you.
For me it's not worth it. (Dell Inspiron B130)
Too much hassle for the wi-fi, in ubuntu i don't need 5mins to set it up on a fresh install.

---

### Post by wjp.reg on 2007-12-03
> **georges023 said:**
> Didn't vote.
Why?
Cause it depends on you.
For me it's not worth it. (Dell Inspiron B130)
Too much hassle for the wi-fi, in ubuntu i don't need 5mins to set it up on a fresh install.

I know where you're coming from; the debian folks, however, would call you a wimp for not wanting to struggle with the installation since, in their perspective, it's the only way to learn linux ;-)

---

### Post by g2g591 on 2007-12-04
I'd say it is based on my about 2 week experiance of upgrading from stable to unstable (which is where ubuntu devs pull ~75% of the packages from, before further stabilizing) One of the main reasons because the upgrade form the default xorg 7.1 from stable to 7.3 in unstable was as simple as "apt-get update && apt-get install xorg-xserver" no need to muss with config files or anything, it just upgraded. But is a bit of a hassle to get the way you want it, like getting it to be have like *buntu and have no root account and use kdesu instead, and I did have to do a little digging on how to get my volume keys set up too (they were buggy in buntu also though)

---

### Post by Ozeuss on 2007-12-06
Debian is definitely worth a try. I have debian installed alongside ubuntu, and it is actually my main OS for about 4 months.
Debian's harder to set up, but of course, more flexible. 
Ubuntu gets a bit boring (package-wise) towards the end of the release cycle, and that's were i enjoy that debian is more like a rolling release.
than again, ubuntu often has newer packages, especially soon after a release. now that kubuntu ships with kde4.0, i might switch back to ubuntu for a while.

---

### Post by Ozeuss on 2007-12-06
duplicate.

---

### Post by areteichi on 2007-12-09
testing doesn't have OpenOffice 2.3 yet while gutsy does.
so at least in some respects, ubuntu is more up-to-date (if not in many respects). I'm actually thinking of going back to ubuntu from testing.

---

### Post by Antman on 2007-12-09
> **byagietera said:**
> testing doesn't have OpenOffice 2.3 yet while gutsy does.
so at least in some respects, ubuntu is more up-to-date (if not in many respects). I'm actually thinking of going back to ubuntu from testing.

Try Sidux first then. It's definitely worth a try. :guitar:

---

### Post by b9anders on 2007-12-11
> **byagietera said:**
> testing doesn't have OpenOffice 2.3 yet while gutsy does.
so at least in some respects, ubuntu is more up-to-date (if not in many respects). I'm actually thinking of going back to ubuntu from testing.

If it is just *some* newer packages you require, it's easier to just pull them in from sid.

It's you want all new, sid + the smxi script allows for a good life on the bleeding edge.

---

### Post by markharding557 on 2008-01-09
i have found debian to be faster,this may be because it has a k7 kernel for k7 processors.
i'm using lenny with some sid packages like nautilus 2.20.0,iceweasil, icedove and others.
nvidia drivers were reasonably easy using their installer but i'm a fairly experienced user
otherwise much like ubuntu

---

