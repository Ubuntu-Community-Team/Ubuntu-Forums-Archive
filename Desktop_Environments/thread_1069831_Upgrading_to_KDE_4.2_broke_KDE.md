---
title: "Upgrading to KDE 4.2 broke KDE"
date: 2009-02-14
forum: Desktop Environments
---

### Post by skullmunky on 2009-02-14
I'm running Kubuntu 8.10 Intrepid.  Eager to savor the crispy excellence of KDE 4.2, I followed the instructions to upgrade KDE from the experimental repository on the Kubuntu site.  Now when I try to log in, the session dies and returns to the login screen.  I figure there was a package conflict or something in the process; now, how do I fix it?  

I read the warning in the instructions about how you have to uninstall any plasmoids before doing this, because they're not compatible with 4.2.  It didn't say -what- specifically you have to remove, though; I removed everything that had "plasma" in the name, but maybe I missed one.

Ok, so I logged into Failsafe Mode, ran synaptic, fixed all the dependency errors and broken packages, so everything looks clean.  KDE starts up now, but when the desktop should appear I get a black screen.  hmm ...

Oh.  rebooting fixed that.  That all took about 15 minutes to from completely ruined to completely fixed, and it didn't require anything particularly elite :)

---

### Post by CyberAngel on 2009-02-21
I already had KDE 4.2 installed but not used it since 8th of February cause I was away.
Today that opened again my pc and did a dist-upgrade to my system, I have the same problem. When I try to login, the session dies and returns to the login screen (KDM).

I renamed ~/.kde to ~/.kde-backup (just to reset the settings if there was to be any problem with some plasmoids or anything else) but I have the same problem.

There is no conflict with the installed packages for me that it can be fixed by running the "apt-get -f install" command...

---

### Post by CyberAngel on 2009-02-21
Problem solved for me too...
It was just some faulty packages in the repositories. I just did another dist-upgrade now and everything is working fine :)

---

