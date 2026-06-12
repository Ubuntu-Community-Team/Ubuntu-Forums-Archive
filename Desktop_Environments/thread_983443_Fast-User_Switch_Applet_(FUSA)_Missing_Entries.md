---
title: "Fast-User Switch Applet (FUSA) Missing Entries"
date: 2008-11-15
forum: Desktop Environments
---

### Post by LordKelvan on 2008-11-15
Hi:

I recently did a fresh install of 8.10, and I must say I am very impressed.  Boot-up time seemed to have improved significantly, setting up the printer was insanely easy (it automatically detected the printer and installed the driver), and setting up dual-monitors was pretty painless (although I did have to use a combination of the Catalyst Control Centre and the Screen Resolution utility).

However, I'm having a problem with FUSA.  Recently, I noticed that it was missing entries.  It now only has 3 entries: "Guest session", "Lock screen" and "Log out".  It is missing the power management entries, and the entries for "Shut-down" and "Restart".  I first noticed it after installing a new theme (Shiki-Colours), but I've since reverted to the default Human theme and the problem still persists.  Of course, being a fresh install, I've been doing a bunch of customizations, so it might not be theme-related.

The weird thing is that if I switch to a Guest session, FUSA will correctly display all entries.  However, FUSA will only display 3 entries when I switch back to my session.

I've tried the following 2 things, but neither worked:

1) re-installing FUSA
2) removing it from and re-adding it to the panel

Any help would be appreciated.

Cheers,
LK

---

### Post by LordKelvan on 2008-11-16
Hi:

Looks like I found the root cause: I had disabled the power management daemon from starting up when booting (by unchecking its entry via System -> Preferences -> Sessions).  To get the missing entries back, I removed FUSA from my panel, started up the power manager (gnome-power-manager is the program name), and then added FUSA back.  In order to make the change permanent, I've enabled the power management daemon to start-up when booting (i.e., checked its entry via System -> Preferences -> Sessions).

I suspect the problem is that without the power manager, FUSA will not display "Suspend" and "Hibernate" (do those options require the power manager?), and will basically fail to display all following entries, which happen to be "Shut down" and "Restart".  This would seem to be a bug, since power management should have nothing to do with shutting down or restarting the computer.  In addition, FUSA should show warning/error messages when it cannot display certain entries so that the user is not confused.  I think I'll file a bug report.

Cheers,
LK

---

### Post by labrekke on 2008-11-24
Hi.

I have a similar problem: The FUSA ( Fast-User-Switcher-Applet ) won't show the statuses "Available", "Away", "Busy", "Offline" or the option "Lock Screen" as displayed in the image below. 

I think I was asked a question about upgrading FUSA that I declined when upgrading to 8.10, but I can't really remember what it was and how I can get it back. Does anyone know? It seems I still have the same FUSA as I had in Ubuntu 8.04.

[IMG]http://labrekke.com/fusa.png[/IMG]

---

### Post by LordKelvan on 2008-11-25
Hi:

I am by no means an expert, but I think the "Available", "Busy", etc. entries only appear if you have Pidgin running (since those entries pertain to your IM status).  I'm not sure about the "Lock Screen" entry though.

If you are concerned about not having the latest FUSA (although you should if the upgrade went correctly), you can go to System -> Administration -> Update Manager, and click the "Check" button.  This will check for updates to any of your system packages, and you can scan the list it returns (the list will be empty if your system is up-to-date) to see if FUSA needs to be upgraded.

Lastly, I think during the upgrade, Ubuntu will ask you whether you want to replace the old shut-down applet with the new FUSA applet.  This may be the question you are thinking of.

Cheers,
LK

---

### Post by labrekke on 2008-11-25
You are quite right, LK. I was thinking that the status option would be available for use with other instant message systems like aMSN, emesene (which I'm using now) or Skype as well, but that wasn't the case. Thanks for explaining. :-)

---

### Post by diaz8 on 2008-12-04
Is anybody experiencing this problem?
When starting pidgin the different states appears in FUSA but with no icons. Attaching pic.... 

Any idea?

---

### Post by mtbsoft on 2008-12-29
> **LordKelvan said:**
> I've tried the following 2 things, but neither worked:

1) re-installing FUSA
2) removing it from and re-adding it to the panel

I recently lost my FUSA icon from my panel (though I'm damned if I know how) and can't work out how to add it back in.

I've tried reinstalling FUSA but that made no difference, could you please outline how you added it back, I cannot find it in the Add to Panel list of options.

---

### Post by mtbsoft on 2008-12-29
Ok, so now I feel a right twit.  I discovered that it is the User Switcher entry available in the Add to Panel menu - just didn't make the connection.  My excuse is that it's late, I'm tired and have a migraine coming on...

---

### Post by mattm591 on 2009-02-19
> **diaz8 said:**
> Is anybody experiencing this problem?
When starting pidgin the different states appears in FUSA but with no icons. Attaching pic.... 

Any idea?

I am having that exact same problem, but only on my second monitor.

Did you ever find a fix?

---

