---
title: "Evms 2.5.3"
date: 2005-11-18
forum: Closed Requests
---

### Post by The Belgain on 2005-11-18
Hi there,

I've just posted a request for this in the mailing lists... should really have read the FAQ first and posted it up in the forums instead.

EVMS 2.5.3 (the latest stable version) has several fairly critical fixes, including some fixes to RAID5 array corruption.  Would it be possible to backport this to Breezy, as it's probably one of the harder programs to install for people not very familiar with Linux.

And keep up the good work...

---

### Post by The Belgain on 2005-11-19
I should probably have mentioned this request comes after some discussion with EVMS devs on the EVMS mailling list. Read through the thread entitled "Possible to create a degraded RAID5 array with EVMS?" in the evms-devel mailing list: 
[http://marc.theaimsgroup.com/?t=113201332100001&r=1&w=2](http://marc.theaimsgroup.com/?t=113201332100001&r=1&w=2)  

EVMS 2.5.3 is currently in Dapper, so presumably it wouldn't be too hard to backport to Breezy?

---

### Post by jdong on 2005-11-20
Accepted

---

### Post by The Belgain on 2005-11-21
Great, thanks for agreeing to backport this one.

I can't see it yet in the backports repository; has it been added yet, or does acceptance just mean that someone will start the backport process?  Any idea when it's likely to be available?

---

### Post by jdong on 2005-11-21
James has actually filed this into the building system already (this is the first time I've heard from him since Backports started)

But once Backports team gives the archive admin (James in this case) approval, the package will get enqueued for build and auto-uploaded subsequently. The ETA on arrival into the archives is not predictable by me.

---

### Post by The Belgain on 2005-11-23
Great.  I've updated to the latest version in the backports repository (using Synaptic) without any problems.

Works fine, and fixes the corruption problems I'd been seeing.  Good job!

---

### Post by The Belgain on 2005-12-10
Well, a new version of EVMS (v. 2.5.4) has just been released.  What's the process for backports - do backports automatically pick up the latest version of packages, or do they need to be updated manually?  Or do backports packages get picked up from the Dapper repository?

Maybe it would be a good idea to upgrade EVMS to the latest version?  It's the kind of package where new versions tend to be bugfixes rather than feature enhancements, and therefore probably a good idea to keep it up to date as bugfixes are quite important for this kind of program.

I've compiled the latest EVMS with the extra patch for creating degraded arrays (this patch didn't make the release, but is not destabilizing, and is official - in the patches section of the EVMS website).  It seems to be working fine for me on Breezy.  Slightly OT, but how do I go about uninstalling the previous version of EVMS from Breezy?  I've got both versions at the moment, and don't want the system to get confused.  Can I just remove it from Synaptic?

---

### Post by jdong on 2005-12-10
Typically, newer versions are requested upon Dapper's inclusion.

For things like Evms, which are fairly core/essential (in fact, broken EVMS = no boot), I'd rather not backport it unless there is a good reason for it. With 2.5.3, the reason was convincing. With 2.5.4, not yet.

Even if it's just "bugfixes" and "minor updates", there is still the chance of system breakage.

---

### Post by The Belgain on 2005-12-10
Sounds fair enough.

Is there any instructions/FAQ about how to move to a latest version of EVMS manually (i.e. compiling from latest source)?  What do I need to do to remove the old version properly before replacing it with the new one?

Will removing it in Synaptic work?  It's telling me I need to remove the 'ubuntu-standard' package.  If not, is there some other way of uninstalling?  Will an unmodified (i.e. just compiled from latest source) EVMS work in Ubuntu?

---

