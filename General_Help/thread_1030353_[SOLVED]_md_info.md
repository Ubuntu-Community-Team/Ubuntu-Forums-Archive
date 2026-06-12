---
title: "[SOLVED] md info"
date: 2009-01-04
forum: General Help
---

### Post by Kissell on 2009-01-04
I was using the computer, copying some files to a software raid created with mdadm, and everything was fine...  

Then I got an e-mail notification from the mdadm daemon while using the disks...  it said that the array had started rebuilding.

That doesn't make any sense to me...  There were X disks in the array before and there are still X disks in the array now...  no disks are failed...  it just for some reason decided to start resyncing the array for no apparant reason.

Is there some way I can find out more information about what happened?

---

### Post by fjgaude on 2009-01-04
Goah, I know of no way, other then doing disk dianostics on a disk-by-disk basis. If everything is working okay now I wouldn't worry about it. That alert may have been caused by a random disk error that **mdadm** or **md** caught and is now not there.

---

### Post by Kissell on 2009-01-04
Yeah, but this isn't like the first time this has happened...  this happens to me fairly often on completely different machines...  last night I had it happen to me on two Ubuntu hardy boxes, completely different hardware, but both running Ubuntu hardy and using mdadm for software raid...  and both started rebuilding the array, apparantly for no reason, within 30 minutes of each other... very weird...

Even weirder...  one of the servers rebooted itself when it must have been about 80% away through the rebuild...  the server was sitting idle except for the resyncing...  and when it finished rebooting, it no longer needed to resync...  it now thinks the array is clean and healthy...  but I know it didn't finish rebuilding.  

These are poor man's raids...  made with lots of sata disks...  they work fine for the most part, but odd things like this happen...  and i'm very worried that someday a disk will actually die and while its dead something like this will happen and it'll think a second disk died, and then i'll lose all the data.  In fact, that's happened before, but i was able to force it to reassemble.  I'm just uneasy about its conduct.

---

### Post by fjgaude on 2009-01-05
If you are concerned enough you will backup all important data. I use three levels, one online, another near-line, and the last, off-line. Backups can save you.

I can't think of anything else to suggest other than drives that are flakey.

Good luck!

---

### Post by Kissell on 2009-01-05
I've got a backup, but it's a pain to resort to that...  I'm not really concerned as much as I am curious...  if its going to say there is something wrong, I'd like it to be a lot less vague about it.  At least tell me which disk it thinks is wrong, then maybe I could just go ahead and replace that disk, so put it at the top of the list for being replaced next time I put in some new disks.

---

### Post by fjgaude on 2009-01-05
I guess you have run **fsck** on an unmounted, but assembled array?

What filesystem is on the array?

---

### Post by Kissell on 2009-01-05
I haven't run fsck yet... 

It's actually a brand new XFS file system...  I just rebuilt the array a week ago, and changed to the XFS file system at the time...  it hasn't been down until this...  just copying files back to it.

---

### Post by fjgaude on 2009-01-06
Well, unless and until you run a complete test on each disk I would say you likely have a drive going bad. It happens, especially with these huge drives lately. That's been my observation over the last year or so.

Good luck with the warrenties. I replaced six Seagates last year, one bad after the other, and can say that the same is true for Samsungs. <sigh>

---

