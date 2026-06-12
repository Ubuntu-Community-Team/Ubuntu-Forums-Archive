---
title: "Dell Remastered Ubuntu - for each new release?"
date: 2007-10-08
forum: Dell  Ubuntu Support
---

### Post by mutenewt on 2007-10-08
I'm interested in buying a 1420N but I'm wondering if Dell plans to release remastered versions of each version of Ubuntu as they are released.  In other words, can I look forward to an easy install of Gutsy and its successor?

---

### Post by notwen on 2007-10-08
I don't believe Dell will remaster an Ubuntu image each time a new version is released, as each new version should include new drivers for the newer hardware that is currently available.  Dell's Feisty image was released due to ppl's inability to install the base Feisty image w/o lots of work and they also included some of the fixes/additional packages needed for their machines to run Feisty well.  It is very possible Dell would do this, but I wouldn't count on it.  Just my thoughts on it.

---

### Post by MetalMusicAddict on 2007-10-08
Dell as of yet does nothing to the disks. Actually from what Ive heard the disks they currently ship are vanilla Ubuntu. So you should restore from the restore partition thing they do because _that_ actually reflects what on the system. I also have it on good authority that they will stop shipping disks altogether.

---

### Post by mutenewt on 2007-10-08
MMA - They are currently offering a remastered version of Feisty.

[http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx?CommentPosted=true#commentmessage]("http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx?CommentPosted=true#commentmessage")

---

### Post by MetalMusicAddict on 2007-10-08
Word from a Canonical employee is that these do not ship with their pre-installed systems.

---

### Post by mutenewt on 2007-10-08
Don't care if they ship it that way.  Just want to know if I'll be able to download remastered versions for each upgrade.  A no hassle upgrade including wifi support with WPA guaranteed to work would make Dell a clear choice.

If not and I'm just going to have to do a manual install/config/deal with wifi issues when I upgrade to Gutsy/other releases, might as well buy any laptop.

---

### Post by perryrt on 2007-10-09
As the owner of a ~3 month old 1420n from Dell, I can confirm that both of you are correct. 

Dell makes available a "Dell-specific" CD of Feisty on their tech-support website, and the physical disc I received with my system was a "plain-vanilla" distro (I suspect the same one you'd get from Canonical - there was no Dell branding on it.) Honestly, they probably figured the "reboot-system-saver" part of their job was done by providing a saved copy of the Dell system in a seperate partition on the hard-drive. Neither was there really word one of paper documentation about running Ubuntu in the box. They didn't even spring for a case sticker :( (Course, I fixed that with a SASE to system76, but still, how much would it have cost them! ....)

I thought I saw a rumor on the Dell forum that they would provide a new remastered CD upon Gutsy's release, but I can't find it now, so perhaps that was wishful thinking. In any event, I think **notwen**'s comments are precisely on point - it's doubtful they will release a new distro package with support for hardware they're no longer interested in supporting, if that makes sense.

Heck, as of 10/3/07, they've subcontracted all their tech support to Canonical - which is actually a good idea, but again, calls their support for Linux into question.

Bottom line to the original question - don't count on it!!! The good side of this coin is that while Dell may consider Ubuntu and Linux a small sector of their market, from what I can tell, Ubuntu considers Dell support a Big Deal (for fairly obvious reasons) so there appears to be a better than average chance that your Dell hardware will be supported natively in coming updates and releases.

My only suggestion would be to do what I do with all original drivers (Windows ones, too) - I burn each to their own CD and stick in a file. Then when I need to reuse them, they're ready for me.

---

### Post by ubuntukid on 2007-10-09
Dell did a lot of work to make everything work perfectly. But surely the Ubuntu developers would take Dells improvements and incorporate it into the newest distro themselves. Basicly Dell made a bunch of drivers work for Ubuntu and fixed a few problems, and it would only improve Ubuntu's hardware compatibility to include all these changes in their new version. So, I would expect that the new version of Ubuntu will work just as well with you Dell machine as the Dell version of 7.04. Right?

---

### Post by ÜbuntuMensch on 2007-10-09
I've been using Ubuntu on a 1420 for 2-3 months now and have gone from dual-booting Vista with a Feisty install, then to pre-Beta Gutsy, found salvation in the Remastered Dell Ubuntu Feisty disk, but am now using Gutsy Beta 64 bit...

uhm, anyway, the thing is I don't think they will need to remaster a disk for Gutsy, etc., because everything is by now supported out of the box or very close to it. Except for the webcam, and that looks to be on the horizon. So you can use the standard install, no problem...just Feisty needed a little extra work to get everything running, thus the remasterd ISO.

---

### Post by perryrt on 2007-10-10
Actually, that's a good point - I assume that with a Centrino Duo processor (or processors, depending on the way you look at it) I should be planning to go to the 64-bit version/offering of Gutsy when it arrives, correct? Are there any specific issues with that we should be aware of?

---

### Post by phr0ze on 2007-10-10
Why would you want to install from a disk again. Update manager is going to move you to Gutsy without wiping stuff out. Even if Dell releases a remastered disk, it won't be as easy as update manager.

Also, I doubt Dell can release a remastered disk within two weeks of gutsy release. It'll be November before you see one for Gutsy if they follow any sort of standard configuration management and testing cycle.

---

### Post by ÜbuntuMensch on 2007-10-10
perryrt:

The only issue is that if you read the 64 bit support threads it will look like there is some potential that the install will be difficult and that some software you want to run is not supported on 64 bit architecture.

Both of these concerns are unfounded.

The useful life expectancy paradigm we're all used to is that things work right when you first get them, then gradually become less useful. Eventually you have to buy a new one when your model phases into obsolescence. This happens especially fast with computers. But it seems with Linux OSs, there is a different paradigm: If you have some relatively more advanced technology, it might not work out of the box with the stable OS, but gradually the support will come - faster if you report and work out problems. 

So, again, the remastered Dell Ubuntu was just a stop-gap for issues that have been largely fixed in Gutsy.

And yes, you should take advantage of your 64 bit architecture. It works fine now, and as development continues it will work even better.

---

### Post by perryrt on 2007-10-11
> And yes, you should take advantage of your 64 bit architecture. It works fine now, and as development continues it will work even better.

Sounds good, thanks....and an interesting point of view on Linux.

I think my personal goal for an upgrade to Gutsy will be a month or six weeks after  release - I suspect that any final problems will work themselves out by then.

---

### Post by ebozzz on 2007-10-11
> **perryrt said:**
> Sounds good, thanks....and an interesting point of view on Linux.

I think my personal goal for an upgrade to Gutsy will be a month or six weeks after  release - I suspect that any final problems will work themselves out by then.

I am running Gutsy on 4 desktops and 1 laptop currently. No significant problems other than the volume of updates that are received. I went the network upgrade route from 7.04 to 7.10.

---

### Post by dondad on 2007-10-13
> **mutenewt said:**
> Don't care if they ship it that way.  Just want to know if I'll be able to download remastered versions for each upgrade.  A no hassle upgrade including wifi support with WPA guaranteed to work would make Dell a clear choice.

If not and I'm just going to have to do a manual install/config/deal with wifi issues when I upgrade to Gutsy/other releases, might as well buy any laptop.

I am running an xps410n. I ended up redoing it because I wanted my /home partition to be separate and the original install uses one big one. I didn't want to reinstall from the special partition because I was afraid it might revert to the single partition so I installed the iso from ubuntu and it worked fine except that it would not restart, but would hang at the splash. It shutdown OK. I fixed it by adding "reboot=b" to the kernel options. I am running the gutsy beta right now, and it has the same problem. I added the reboot=b parameter to the default kernel options in grub's menu.lst and life is good.

---

### Post by gbrainin on 2007-10-13
> **dondad said:**
> I am running an xps410n. I ended up redoing it because I wanted my /home partition to be separate and the original install uses one big one. I didn't want to reinstall from the special partition because I was afraid it might revert to the single partition [...]

FYI, the factory-reinstall partition provided by Dell does repartition your drive if you use it.  I tried this as an experiment, and it killed my separate /home partition.

---

