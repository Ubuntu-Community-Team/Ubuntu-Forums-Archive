---
title: "KDE - Icons and widgets disappearing"
date: 2009-04-09
forum: Desktop Environments
---

### Post by Roryking on 2009-04-09
Hey everyone, just made the switch from Ubuntu 8.10 to Kubuntu 9.04 Beta. As you will see in the attached screenshot, after a period of inactivity, all my icons and widgets become invisible (but not unusuable). On this desktop, I have the Weather, Twitter, RSS feed, Network activity applets - also the desktop folder, which is completely invisible.

My only conclusion is that this occurs when KTorrent is running and the computer is idle for an extended period of time. I have tried disabling power management and screensavers, and running kwin --replace does not solve the issue. The only solution is to log out and log back in - fortunately, I don't have to actually restart to bring everything back.

Any ideas?

---

### Post by roblubbers on 2009-04-14
I'd say you should file a bug on launchpad (if it isn't on there already)

---

### Post by Beleggrodion on 2009-04-28
Hi there. I also have the same issue as Roryking. I use the current Kubuntu 9.04 that is now released and not the beta. I can use the widgets and click and right click on them, the work, but ex. configure is not possible anymore. I also checked the logfiles, but there is nothing. 

Have someone now any ideas?

---

### Post by Monsieur Gonzalez on 2009-04-28
Before upgrading to 9.04, which KDE4 version were you using? I've had to remove plasma settings (removing plasma config files from my .kde folder) with each KDE4 upgrade until reaching 4.2, the first considered "stable". I just added the widgets again, placed and customized the panels afterwards.

---

### Post by Beleggrodion on 2009-04-29
Thanks for the tip. I renamed the config files and let kde generate new ones and now it works. I used KDE 4.1 before.

---

