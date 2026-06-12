---
title: "Dell Poweredge 2950: Ubuntu x64 support for SAS 6 I/R controller?"
date: 2010-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yah.shoor on 2010-04-22
It's been a loooong time since I stepped through any sort of Linux install - eight years or more. I've been asked to install Ubuntu Server 9.10 on a Dell PowerEdge 2950 at my workplace, and I've been doing some pre-installation research. Seems to me that the SAS controller in this Dell is a rebranded LSI SAS/RAID controller, and I've been able to find quite a few different threads about this particular controller:

[http://ubuntuforums.org/showthread.php?t=1367857](http://ubuntuforums.org/showthread.php?t=1367857)
[http://ubuntuforums.org/showthread.php?t=664778](http://ubuntuforums.org/showthread.php?t=664778)
[http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114)


Can anyone confirm for me that this configuration won't work? I have two 300gb 15k SAS drives in RAID 1, and most of the solutions I've seen involve using software RAID. I'm working from a Dell spec sheet, so I haven't peeked inside the box to figure out if it has any SATA headers on the mobo - I don't even know what kind of integrated NIC is on it, and I've read about some other issues people have faced when trying to install Ubuntu on this server. 

It looks like a patch made it into the kernel circa 2.6.25 or so, but I'm still seeing posts from people installing recent releases, with problems but no solutions. So, can anyone confirm/deny? Many of the solutions are not written for the, ah, "absolute beginner" (after eight years out of the game, I may as well be one) and I'd really like to discover that my first dip back in the Linux pool was *not* going to involve converting an rpm with alien and recompiling the kernel.

---

### Post by dentaro16 on 2010-06-18
i can confirm that the SAS controller works for ubuntu. we have 2x2950's here. one of them runs ubuntu server cloud with eucalyptus. runs great.

---

