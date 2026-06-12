---
title: "Slow boot time! Argh!"
date: 2008-04-18
forum: Desktop Environments
---

### Post by Drew_[SCED] on 2008-04-18
I've just installed Gutsy on a laptop for a friend of mine.  Everything is working nicely thanks to some help from the IRC, but the boot time is UNGODLY.  I would estimate the time it takes for the laptop to go from being turned on to being at the login screen to be at about 4 minutes.  Furthermore, the Ubuntu logo does not load (you know, the logo with a nice little loading bar?).

I don't think it's the hardware on this machine.  The HDD is a slower RPM and there's not much more than 256MB RAM but I've run Feisty on much lower-end machines with less boot time.  Could anyone give me any answers as to why my boot time puts all others to shame?

P.S. Will [InitG](http://ubuntuforums.org/showthread.php?t=80423&highlight=initNG) work for Gutsy, and will it solve my problem?

Thanks in advance.

---

### Post by mcduck on 2008-04-18
On some setups (usually laptops with widescreen displays) the resolution for the usplash is configured wrong, which cause the boot image to not show and also slows the boot time. Fixing the resolution will solve both your problems.

See this post for instructions how to correct the resolution: [http://ubuntuforums.org/showpost.php?p=4682083&postcount=9]("http://ubuntuforums.org/showpost.php?p=4682083&postcount=9")

---

### Post by mfaust731 on 2008-04-18
um, I hope 256K of ram was a typo....

---

### Post by HerCsD on 2008-04-19
[SIZE="2"]Wow.Just what I needed.I do also have exactly this problem with my laptop as far as the splash screen is concerned but other than that all settings seem to me pretty fine(except when using full screen in video playback :mad:).But I guess if you have laptop issues refer to the specific Main Support Category as this is for Desktop environments(I've actually made the same mistake :-P).[/SIZE]

---

