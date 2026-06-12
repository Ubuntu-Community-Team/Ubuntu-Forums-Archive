---
title: "Mac Mini and Ubuntu"
date: 2006-07-12
forum: Desktop Environments
---

### Post by guest128 on 2006-07-12
Hey there folks. I've been using Ubuntu for a while now, and I'm happy to say that it has, for me, entirely replaced Windows. But I've had this old 700Mhz computer for a while (ever since my nice computer was set was burned up) and I'm thinking about getting a mac mini. They're cool because they're small enough to carry around in a suitcase, but not expensive and easily destroyed, like laptops. I'm almost dead set on it, but I'd really like to know the lowdown on how they perform with Ubuntu. 

I mostly use simple programming IDEs, listen to music, and watch a video from time to time. I am plenty willing to spend time tweaking the OS if that is required for things to work correctly, but please share you experiences with me, pros and or cons. I have no doubt that there are machines with which ubuntu works better, but as of now, I'm focused on the tiny macs.

Thanks for your time,
guest128

---

### Post by aysiu on 2006-07-12
How about a Koala instead?
[http://system76.com/index.php/cPath/2_52?osCsid=f5e77b0fced075a13eb9ace9f1dbcc9b](http://system76.com/index.php/cPath/2_52?osCsid=f5e77b0fced075a13eb9ace9f1dbcc9b)

---

### Post by chasisaac on 2006-07-13
> **aysiu said:**
> How about a Koala instead?
[http://system76.com/index.php/cPath/2_52?osCsid=f5e77b0fced075a13eb9ace9f1dbcc9b](http://system76.com/index.php/cPath/2_52?osCsid=f5e77b0fced075a13eb9ace9f1dbcc9b)

After looking at the system 76 all I can say is cool. I was going to buy my wife a macmini and convert her to linux slowly. But now . .  . I think I need a new laptop

---

### Post by guest128 on 2006-07-13
While the Koala looks cool, I have a general distrust of most minis, due to my terrible experience with the Epia M-1000 mini motherboard. I would like to think that apple kinda knows what they're doing (since their notebooks rock) In any case, while I appreciate the idea, I'm looking for thoughts on the mac mini itself rather than alternative suggestions. I suppose I'll keep the Koala in mind.

So please, keep it on the subject of Ubuntu on the Mac-Mini.

---

### Post by gumbald on 2006-07-13
I am also interested in Ubuntu on a Mac Mini as I am considering replacing my 2nd tower and my G3 B&W to dual-boot on the much smaller device..

How does it perform with things such as XGL?

---

### Post by almahtar on 2006-10-20
It's a bit of a pain to get Linux installed on the Mini (I'm typing on Dapper on my mini right now).  The tutorial I used is at [http://www.bin-false.org/?p=17](http://www.bin-false.org/?p=17)

I got it working with Edgy using Grub, which was preferable to lilo, but I couldn't do the same in Dapper.  Attempting to install elilo always failed for me - I think the EFI was messing with it... it always thought my filesystem was corrupt.

Anyway, if you're interested in putting Linux on a mini I'd say plan on spending a good day doing it.  If it ends up not taking that long then sweet, but I wouldn't want it to take you by surprise.

---

### Post by almahtar on 2006-10-20
Oh, and the performance in XGL/AIGLX is actually really good.

---

### Post by meltingrobot on 2006-10-21
I just got my Mac Mini yesterday.  I'm thinking I might wait until the 26th for Edgy's final release.

---

### Post by almahtar on 2006-10-22
Yeah, may be wise.  It still has a few issues to work out.  A while ago the package manager had a bug in how it figured out what packages were and weren't orphaned, thought everything could be "safely removed" and started just eating itsself.  I finally noticed things were taking too long and stopped it when I saw it was removing Gnome.  Bad idea, package manager.  Even after reinstalling, there were odd broken dependencies, etc.  Yeah, that sucked :-)

---

