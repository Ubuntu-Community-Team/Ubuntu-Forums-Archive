---
title: "speeding up boot-time by reboot &amp; auto-hibernate?"
date: 2009-06-11
forum: General Help
---

### Post by dh003i on 2009-06-11
A friend of mine said that some OEM used a trick to make Winblows boot faster: shutting down would actually reboot the computer and put it into hibernate mode. 

Then when you "boot up" again the next time, you're emerging from hibernation, so you get to a usable desktop faster. 

Any way to do this in Ubuntu?

Also, anyway to make it automatically load the default user's profile, but lock the user, so that after password entry, you're immediately put on your desktop?

---

### Post by WIGGMPk on 2009-06-11
I think you have been bambozeled..

I sincerely doubt its possible (even for an OEM) to have Windows perform the steps you described. I have also never heard of this being possible in Linux.

As for the other questions about automatically logging in as the default user, it sounds possible. I am not sure about the autolock though.

---

### Post by sdennie on 2009-06-11
It would be possible to do this but, it wouldn't be useful in all cases, you would probably need to have a kernel patched with TuxOnIce, it wouldn't be trivial to do and probably poses security risks.  Essentially you would need to intercept calls to shutdown/halt and instead write a flag and reboot.  When the system comes up, from userland, you'd have to direct pm-utils via d-bus to enter a TuxOnIce hybrid-suspend mode.  That writes the hibernate disk image but, instead of shutting down after it's written, it suspends to RAM.  That means if you turn your computer on before the suspend has killed the battery (generally a few days), you will have about a 5-10 second "boot" to a clean desktop.  If you don't turn it on before the battery dies, you will have about the same length of boot or possibly longer as it thaws from hibernation.

You could do this for a personal machine but, you aren't likely to ever recuperate the time you put into making it work by your faster boots.  And, it's not something you would want to deploy on a large scale without putting a huge amount of time into investigating the ramifications of it.

Basically, if your machine supports suspend/resume, why bother to do this in the first place?  This method gives you a slower machine (nothing is cached), you have to re-open all your apps and, if your battery dies before you come back to this setup, you are probably looking at a *slower* boot time.

Edit:
Although, TuxOnIce supports compressed images that include the cache so, maybe the warnings about bad side effects with regard to speed are not warranted.

---

