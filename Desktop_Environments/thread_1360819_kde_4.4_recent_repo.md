---
title: "kde 4.4 recent repo?"
date: 2009-12-21
forum: Desktop Environments
---

### Post by Correnos on 2009-12-21
The kubuntu site offers a repo that let's me upgrade to the kde 4.4 beta. The problem is, that repo is not particularly recent, specifically kwin has a problem in that build that prevents compositing, fixed in a later release. Does anyone know if there is a repository for (k)ubuntu that has more recent builds available?

---

### Post by Zorael on 2009-12-21
Well, the ppa contains Karmic packages of 4.4b1, and 4.4b2 was released just today (21/12). As per normal, I imagine that 4.4b2 sources will be copied from Lucid repos and compiled for Karmic once/if deemed bug-free enough.

That said, no; I don't know of any alternative repos.

---

### Post by brommage on 2009-12-22
Short of building from scratch, I'm not sure that you'll be able to get the 4.4 betas except from the repos (in *buntu, anyway).  

Check out 4.4 b2--compositing is supposed to be fixed in this new version (although, I can't tell, since my compositing didn't get messed up on upgrade to 4.4 b1).

---

### Post by Zorael on 2009-12-22
The ppas have beta 2 packages now.
```
$ apt-cache policy kdebase-bin
kdebase-bin:
  Installed: 4:4.3.85-0ubuntu1~karmic1~ppa1
  Candidate: 4:4.3.85-0ubuntu1~karmic1~ppa1
  Version table:
 *** 4:4.3.85-0ubuntu1~karmic1~ppa1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     4:4.3.4-0ubuntu1~karmic1~ppa1 0
        500 http://ppa.launchpad.net karmic/main Packages
     4:4.3.2-0ubuntu3 0
        500 http://se.archive.ubuntu.com karmic/main Packages
```
4.3.80 is beta 1, 4.3.85 is beta 2.

---

