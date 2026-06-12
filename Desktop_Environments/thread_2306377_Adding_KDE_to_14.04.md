---
title: "Adding KDE to 14.04"
date: 2015-12-15
forum: Desktop Environments
---

### Post by grathbun on 2015-12-15
I installed Ubuntu Studio 14.04_64 bit; I prefer KDE, so also installed the **kde-full** meta package after reloading the repository data in Synaptic.
However, now that I've installed it, how do I get X to come up in KDE instead of in Ubuntu's default desktop environment?  In other distros
I've used in the past, there was a drop-down list on the login screen allowing me to select the DE, but not here.

There's no option to choose KDE in **Settings-->Session and Startup**, but I have **Launch KDE services on startup** checked 
in **Session**'s **Advanced** tab.

I also noticed that there's now a new icon in the Settings Manager for KDE System Settings, but nothing happens when 
I click it (except the icon is selected.)

Any help much appreciated.  (I have a metered internet connection, so downloading **Kubuntu** and then adding the Studio apps would be prohibitively
expensive and not a reasonable option.)

- grathbun

---

### Post by egeezer on 2015-12-15
I don't know how big the kubuntu-desktop is in megabytes, but that's what you need - the meta package is just the wrapper for it.

```
apt-get install kubuntu-desktop
```

is what you need; if it is anything like xubuntu-desktop, it will run about 300MB.  It contains all the Kubuntu-specific things and will give you that little icon you need just above the login line.

---

### Post by grathbun on 2015-12-16
Thanks, egeezer, I'll give that a shot and post the results.

---

### Post by grathbun on 2015-12-18
egeezer,
It worked -- thanks again!

---

