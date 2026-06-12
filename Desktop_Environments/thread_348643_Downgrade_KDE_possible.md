---
title: "Downgrade KDE possible?"
date: 2007-01-29
forum: Desktop Environments
---

### Post by tictacman on 2007-01-29
Hi folks, I knew it would happen, I mashed my kubuntu setup by trying to remove kde.3.5.6 after experiencing a number of crashes.  It's pretty much useless right now.  I thought I'd just go into /var/cache/apt/archives and just by clicking on  kde3.5.5 packages,3.5.6 packages would be magically uninstalled and broken packages righted :).

Question is, what is the right way to downgrade from  kde?  I don't want this sort of thing to happen again.

---

### Post by Ramses de Norre on 2007-01-29
```
sudo aptitude install kubuntu-desktop/edgy
```
Will downgrade kubuntu-desktop to the version in edgy's main repo. You can then disable the repo you don't like and update to get the version from edgy-updates or something if there is one in there.
Maybe it's better to replace kubuntu-desktop with kde-core or something, I don't really know which package you upgraded and replace "edgy" by "dapper" if you're on dapper.

---

### Post by tictacman on 2007-01-29
Actually I added a 3.5.6. repository to sources.list then sudo apt-get update
 sudo apt-get dist-upgrade. So I pretty much upgraded everything that could.  Thanks for respsonse I will use the command you suggested.

---

### Post by mexlinux on 2007-01-29
I also upgraded to kde 3.5.6 , but I'm not experimenting any problem.
Also, yesterday some more kde packages where updated, maybe they solve the problems...

---

