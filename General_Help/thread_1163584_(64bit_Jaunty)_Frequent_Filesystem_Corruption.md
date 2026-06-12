---
title: "(64bit Jaunty) Frequent Filesystem Corruption"
date: 2009-05-18
forum: General Help
---

### Post by eyefragment on 2009-05-18
Recently, my filesystem (ext 3) has been becoming corrupted while Jaunty 9.04 is running.   Things run just fine, and then firefox locks up (and refuses to restart, claiming that an instance is already running), new windows open up blank, and when I try to reboot, it says that the program "unknown" is not responding.  

Upon reboot, filesystem inconsistencies are discovered, and a fsck has always fixed them (about 20 times or so, at this point).  Sometimes there are inconsistencies in the boot block, and I need to boot off of a liveCD  to run the fsck, but I have not yet lost any data.

I used smartmontools to check the S.M.A.R.T. status of my hard drive, and while I don't understand most of the details of the self test, it says that SMART overall-health self-assessment test result: PASSED, so I don't believe that this is a physical hard drive issue.

I am actually preparing to do a clean install, so I can do pretty much anything to fix this issue, but I need to figure out what to do. =p.  Any ideas for a fix, or pointers to where I can ask for better advice?

Note: this seems to be the same issue reported here ([http://ubuntuforums.org/showthread.php?t=1149563&highlight=filesystem+corruption](http://ubuntuforums.org/showthread.php?t=1149563&highlight=filesystem+corruption)), but there didn't seem to be any suggested fix, so I'm testing the waters here.

---

### Post by quixote on 2009-05-18
I have the exact same behavior, also using 64-bit jaunty. I actually filed a bug report about it ([https://bugs.launchpad.net/jaunty-backports/+bug/372526](https://bugs.launchpad.net/jaunty-backports/+bug/372526)) since it obviously wasn't normal behavior or something to do with hardware failure.

It's very frustrating.  Can't use jaunty because of it, since I never know when it's going to lock up on me and require a filesystem fsck rebuild!

My system: CPU: P8400 Core 2 duo 2.26Ghz;  Graphics: integrated Intel GMA X4500; 4GB RAM

---

### Post by eyefragment on 2009-05-19
I'm glad that you've put up a bug report on this.  I myself rarely file bugs under launchpad, since I never know where to actually categorize bugs (this one, in particular, could be due to any one of a million components).  In any case, I'll be watching this thread and your launchpad report to see if there's anything that I can report in order to help.

In case you need them, here's everything that I can think of that could possibly be relevant regarding my specs:

Processor: Intel Core 2 Duo @2.27 gHz (not sure what the model is, but I can look it up)
Graphics Adaptor: ATI Radeon HD 3450 (running over an expresscard/34 slot that's pretending to be a PCI-X slot for these purposes)
OS:  64 bit Jaunty Jackalope
Filesystem type:  ext3 (running on a 200gb 7200 RPM drive, but that almost certainly is irrelevant)

---

### Post by quixote on 2009-05-19
I was thinking maybe it was my Intel graphics that was causing the problem, but I see you have ATI.  How much RAM do you have?  Maybe more is worse here, who knows.

Me filing a bug report is kind of silly, because I too have no idea how to categorize it.  But it seemed to me such an important issue that the devs need to pay attention.  Aside from us poor schmoes with the hosed inodes, the first time this happens to some tech reviewer with an audience, it'll be an incredibly black eye for ubuntu.  I hope they get it sorted out before that happens!

Do you want me to add your specs in a comment to the bug report?  Or do you have / are willing to get a launchpad account?

---

### Post by eyefragment on 2009-05-19
I have a launchpad account.  I'll add my specs to the bug report in a bit.  For reference, I have 4gb of ram, but I think that's pretty common nowadays.

---

### Post by quixote on 2009-06-01
Looks like [we may have a fix]("http://ubuntuforums.org/showpost.php?p=7382178&postcount=29").  It involves upgrading the kernel on the jaunty install, but that's surprisingly easy to do.  At least, it was surprising for me!

---

### Post by nimrod_abing on 2009-06-14
I experienced this very same bug when I upgraded my laptop from Interpid to Jaunty two days after it was released. I have since rolled back to Intrepid. I was planning to do a clean install of Jaunty just now and had started downloading the ISO images. Good thing I searched around the forums and found this thread. It looks like the issue is still there even with a clean install so I won't bother with Jaunty and just wait for the next release.

<rant>
My Acer Aspire 4920G laptop which had been working very well on Interpid Ibex until I did a network upgrade to Jaunty Jackalope. A couple of things broke but I was able to quickly fix them. But then it kept locking up and I kept getting fsck errors on reboot. There were also times when I did a proper shutdown and on cold start, it would tell me one of my partitions were not unmounted cleanly and then proceed to fsck. There were times that shutdown would completely lock up and I had to hold the power button down to force it to turn off. I kept losing files on my / partition and worst of all I also lost a couple of files on my /home partition. It was like Jaunty Jackalope was playing Russian Roullette with my data.

I began to suspect that it was due to the needless tweaking of boot/shutdown scripts (and parts of the kernel) that Ubuntu team had been doing so that Jaunty Jackalope will boot/shutdown faster. It seems to me that the Ubuntu team has been focusing way too much on frivolous things like having the fastest boot time and less on system stability. I don't really care if my computer will boot/shutdown in 5 seconds or 5 minutes. Boot/shutdown is something that I normally do **once a day** and all I really care about is how stable my system is in between boot and shutdown. Having a fastest boot/shutdown is totally irrelevant to my productivity though I would be glad to have a fast boot/shutdown, I don't think it is worth the risk of losing my data.

To date, there has been no **official fix** for the issue (the PPA kernel in this thread does not count). I remember _[one bug in Intrepid Ibex that took **6 months** to fix]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285")_. That particular bug was really difficult to reproduce so I really doubt that this issue in Jaunty will be resolved any time soon.

I have been using Ubuntu since the first release (4.10 Warty Warthog) and I have used **every single release** since then. Thus far, Jaunty Jackalope, is the absolute worst release to date. The name seems pretty appropriate though, as a "Jackalope" is really just a _[horribly disfigured rabbit]("http://ww2.lafayette.edu/%7Ehollidac/jacksforreal.html")_.
</rant>

With regards to this bug, this appears to have been a known issue **since November of last year** (see [http://lkml.org/lkml/2008/11/14/121](http://lkml.org/lkml/2008/11/14/121)) and appears to have been fixed with this kernel patch [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=commit;h=b29e79bf557ce777878518da154f4a0becb1de0e](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=commit;h=b29e79bf557ce777878518da154f4a0becb1de0e) and it was applied to kernel 2.6.28-9 during development. However it seems that 2.6.28-11 had regressions and the bug manifested itself again. Note that this was **a known bug** months prior to Jaunty Jackalope official release and although it was marked as "Critical" (and **unresolved**) in Launchpad, Jaunty Jackalope was released to the general public nonetheless.

---

### Post by steffan72 on 2010-01-08
well it appears the problem is not limited to Jaunty as i am having the same problem with Karmic.  Looks like it may be time to re-install...........and if it happens again then i am goin to go back to windows.............i can't keep goin through this all the time

---

### Post by quixote on 2010-01-09
I'm running 64-bit karmic on the same machine that had filesystem corruption issues with the 2.26.28-11 kernel.  So far (about three weeks now) it's been very stable.

I also haven't seen any other reports of that same problem cropping up, so you may want to check your hard drive.  Hard drive failure can have much the same symptoms: increasing frequency of random filesystem corruption events.  The difference, of course, is that moving to Windows will cure the problem if it's Ubuntu's fault, but cause complete data loss if it's the HD.  (The more disk accesses, the sooner the disk fails, and installing is a *lot* of accesses.) 

As far as the Jaunty bug is concerned, I really have to agree with nimrod_abing. > this was a known bug months prior to Jaunty Jackalope official release and although it was marked as "Critical" (and unresolved) in Launchpad, Jaunty Jackalope was released to the general public nonetheless. I never would have thought Ubuntu would do that, and it's really bothered me.  I, too, have been an enthusiastic user for years, since the Dapper days.  They could have AT LEAST had a warning message on the 64-bit installation iso's!

---

