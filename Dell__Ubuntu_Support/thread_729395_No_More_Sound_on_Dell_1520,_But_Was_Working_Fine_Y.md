---
title: "No More Sound on Dell 1520, But Was Working Fine Yesterday"
date: 2008-03-19
forum: Dell  Ubuntu Support
---

### Post by trmentry on 2008-03-19
I've been running Gutsy on my 1520 for 3 months now and not had any issues.  I followed the guide about using the backports-modules-generic to get sound work and it was, till today.

I boot up my laptop and no sound.  I thought it odd that it was muted when I booted it up. The little speaker in the notification area showed that.  So I unmuted and put volume up to 100% but still no sound in anything.

I rebooted and same dealio.  Booted into Vista, and its fine... sound is ok.  So its not hardware.

Figure something is wacked but haven't changed anything in a long time, and was working yesterday on the train fine.  So I complete removed the modules and rebooted and then reinstalled and rebooted and ran the steps again in the guide.

Still no joy.


Anyone have any ideas why my sound which was working yesterday without issues all of a sudden with no changes to the laptop isn't working?  I'm at a complete loss and really don't want to reinstall.  

Thanks

---

### Post by sdennie on 2008-03-19
I don't know how often you reboot the machine but, it's possible that you had a pending kernel update and, upon reboot, it clobbered the backports-module-generic changes and you are only now seeing the effects.  You could try to remove and then re-install the backports-module-generic .deb that you got from Dell and see if that fixes the problem (maybe see if there is an update first).

---

### Post by trmentry on 2008-03-19
I reboot the laptop 2 or 3 times a day when I shutdown before to take it to work, then at work, then on train.

I didn't get the deb from Dell.  Its in apt.  At least the one I used.

Any other ideas?  Or things to look for?

---

### Post by sdennie on 2008-03-19
You're laptop isn't one of the Ubuntu pre-installed models that are available but, it's quite close to the 1525n.  Dell has a lot of info about fixing linux problems at: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) and, specifically, you may want to see if the advice at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Sound_Muted_After_Resume](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Sound_Muted_After_Resume) helps to fix your problem.

---

### Post by trmentry on 2008-03-19
No its not the preinstalled version of a Dell.  The reason is I didn't like the specs of those laptops.  So spec'ed out a 1520 that had hardware that was friendly to Ubuntu.

Thanks for the links.  I'll cehck them out and report back.

---

### Post by trmentry on 2008-03-19
Well I completely removed my backport-modules that I installed from apt.  And rebooted.

Then install Dell's version.  

The sound was so loud after the reboot I thought I was going to blow those little speakers out.

Not sure what or better yet why I had to do that as I never suspend or hibernate. Just shutdown, but thanks for the help.

---

### Post by sdennie on 2008-03-19
> **trmentry said:**
> Well I completely removed my backport-modules that I installed from apt.  And rebooted.

Then install Dell's version.  

The sound was so loud after the reboot I thought I was going to blow those little speakers out.

Not sure what or better yet why I had to do that as I never suspend or hibernate. Just shutdown, but thanks for the help.

I dunno either.  The "backport" part of the package name leads me to believe that it probably contains a newer version of the ALSA drivers than what is installed by default.  I'd keep the Dell link handy because it's possible that a kernel update will clobber your driver again.

---

