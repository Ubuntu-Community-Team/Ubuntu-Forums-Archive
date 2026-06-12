---
title: "lubuntu-desktop install error in Ubuntu 10.04"
date: 2011-12-23
forum: Desktop Environments
---

### Post by Jeandré on 2011-12-23
Using Ubuntu 10.04.3 amd64 with Xfce 4.6.1.

When trying to install lubuntu-desktop 0.13 from Ubuntu software center with the Ubuntu 10.04 CD in, I've been getting 

"Failed to download package files

Check your Internet connection.

Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_15.0.874.106~r107270-0ubuntu0.10.04.1_amd64.deb Connection failed [IP: 91.189.92.167 80]"

**Suggestions on ways to get lubuntu-desktop or some other way to try out LXDE on top of my Ubuntu setup?**



Other DE/WM suggestions welcome. I've been happy with GNOME 2 since before moving to Ubuntu 5.04.

GNOME 3/Unity: I'd rather have my fingers amputated with a fork.

MATÉ: I prefer Xfce.

KDE: I don't think it'll work well on my slow PC, and I want to run the same DE on it and my faster laptop. 

Xfce: I like it, and have been using Xubuntu 11.10 on my laptop, but 4.6.1 is a bit cruftie on top of my Ubuntu 10.04 setup.

---

### Post by Dennis N on 2011-12-23
For one thing, the version in the Lucid repository is not up to date. The current one is 0.28. So you would not be seeing what improvements the current version brings. So keep that in mind.

The chromium-browser package is shown as a dependency, so that failure to retrieve it is causing the problem. You might try to install the chromium-browser separately first, then lubuntu-desktop.

Ideally, trying and then installing the newest version from the Lubuntu Live CD is the best way to experience Lubuntu.

Good Luck.

Note: Chromium-browser is NOT a dependency of the current lubuntu-desktop ( 0.28 ), but is for the old Lucid version of lubuntu-desktop (0.13).

---

### Post by Jeandré on 2011-12-24
> **Dennis N said:**
> For one thing, the version in the Lucid repository is not up to date. The current one is 0.28. So you would not be seeing what improvements the current version brings. So keep that in mind.

The chromium-browser package is shown as a dependency, so that failure to retrieve it is causing the problem. You might try to install the chromium-browser separately first, then lubuntu-desktop.

Thanks. I tried to install chromium-browser 15 from Ubuntu software center, and got the same error - which made sense after I got the error. Lubuntu 10.04 doesn't seem to be an LTS as stated at [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal).

> **Dennis N said:**
> Ideally, trying and then installing the newest version from the Lubuntu Live CD is the best way to experience Lubuntu.

Good Luck.

Note: Chromium-browser is NOT a dependency of the current lubuntu-desktop ( 0.28 ), but is for the old Lucid version of lubuntu-desktop (0.13).

I have a download limit, which is why I'm not downloading the entire new Lubuntu distro iso, and am trying to just add lubuntu-desktop to Ubuntu 10.04.

Instead of adding a daily chromium repository, I decided to try ppa:lubuntu-desktop/ppa ([https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)): 
Ubuntu software center, 
Edit, 
Software sources, 
Other software, 
Add, 
ppa:lubuntu-desktop/ppa, 
Close, 
waited for cache to update, 
still not lubuntu-desktop 0.28, 
File, 
Close, 
Update manager, 
Check, 
Close, 
Ubuntu software center, 
lubuntu-desktop (0.14), 
Install, 
same error.

I'll wait for my download to top-up, then install Xubuntu 11.10 from CD on my old PC and update it. At my next download top-up, I'll see if I can get the Lubuntu 11.10 iso and try that.

Thanks again.

---

