---
title: "upgrading after automatix"
date: 2006-08-28
forum: Desktop Environments
---

### Post by bazder on 2006-08-28
Hi,

I just installed Dapper on a laptop and am thrilled that everything
works including widescreen, WPA, and all the bells & whistles so
easily added with automatix.

Question: is it advisable to comment out the automatix source.list
entry and run update/upgrade *OR* better to leave it uncommented
and do update/upgrade when the time comes?  Which is more likely
to break stuff?

many thanks,

bazder

---

### Post by eternalsword on 2006-08-29
well since you already have non-default stuff installed, it probably doesn't matter.  things may break in either case.  i typically open up synaptic when the system tells me of upgrades and mark the upgradable components by hand to check for incorrect dependencies.  of course i'm running about half dapper and half edgy now, so inevitably i end up with some broken pieces here and there but nothing i haven't been able to work around.  i will tell you this though, if the marillat repository was added by automatix, i'd comment that one out.  it has some debian only packages in it, which i learned the hard way when m4a's wouldn't play in rhythmbox due to a libfaad upgrade.

---

