---
title: "Kmenu Disappeared"
date: 2005-05-12
forum: Desktop Environments
---

### Post by HarryS on 2005-05-12
Installed Kubuntu day befoe yesterday.  Neat install, everything worked great.
Yesterday installed more software and started configuring things.  Upgraded everything and changed the splash screen before turning the machine off.

This morning when I turned the thing on I got a "wizard" that would help me configure KDE.  Figuring I had nearly everything done I skipped the wizard.

I first noticed the #1 desktop background had disappeared.  All the applets were gone from the panel - easy enough to bring back.  The application I had added to the panel were still there, and the ones I have removed were still gone.

BUT!!!
The KDE menu is gone and so is the application that contains Konqueror file manager, far places, and a couple of other things.

How do I put these items back in the panel?????

How can I get that "wizard" so show up again.  Maybe that magic will install the menu and whatever else has gone into limbo land.

Harry S

---

### Post by HighKing on 2005-05-12
I've had the same problems a few days ago.  It seemed one of the updates didn't install correctly (some files couldn't be overwritten, so the updater figured not to install the package at all)

Problem is that this was an important package for the KDE system (don't remember the name of this package anymore).

Since I didn't have time to figure things out, I've reinstalled Kubuntu, but haven't updated the system yet since I'm affraid things won't work after the update...

---

### Post by HarryS on 2005-05-12
Stupid me!  These Items are in the "Special Button" under "add to panel."

Still, it is panic and almost heart attack time when stuff desappears for no apparent reason.

I'd still like to know how to get that "wizard" back.

---

### Post by wwwolf on 2005-05-12
[QUOTE=HighKing]I've had the same problems a few days ago.  It seemed one of the updates didn't install correctly (some files couldn't be overwritten, so the updater figured not to install the package at all)

Problem is that this was an important package for the KDE system (don't remember the name of this package anymore).

Since I didn't have time to figure things out, I've reinstalled Kubuntu, but haven't updated the system yet since I'm affraid things won't work after the update...[/QUOTE]

That update file is kdelibs-data and I have learned to stay away from it! bringing things back on the menu is no real problem, and you can always run 'kmenuedit' in the konsole. I had to reinstall because I could no longer mount removable media (thumb drives, CDs etc.)

You can force the install of kdelibs-data but those that have done so later post that they regretted it.

HTH,

---

### Post by wwwolf on 2005-05-12
[QUOTE=HarryS]Stupid me! 
I'd still like to know how to get that "wizard" back.[/QUOTE]

It took me several days to find it. Run 'kpersonalizer' in the konsole.

HTH,

---

