---
title: "Synaptic issues..."
date: 2005-10-30
forum: Desktop Environments
---

### Post by Techno_Monkey on 2005-10-30
Hi all

Just re built my Ubuntu machine... and now when I go into the Synaptic Package Manager and use the search function I get no results for mplayer or qtparted (both were there yesterday before the re build).

Can anyone shed any light on this for me??

Many Thanks
Darren

---

### Post by Xian on 2005-10-30
They are in the universe/multiverse repos.
Do you have these in your sources.list?

[Adding Repositories in Ubuntu](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

```
$ apt-cache policy mplayer-386
mplayer-386:
  Installed: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Candidate: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Version table:
 *** 1:1.0-pre7cvs20050716-0.1ubuntu9 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
$ apt-cache policy qtparted
qtparted:
  Installed: (none)
  Candidate: 0.4.4-4ubuntu1
  Version table:
     0.4.4-4ubuntu1 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
```

---

