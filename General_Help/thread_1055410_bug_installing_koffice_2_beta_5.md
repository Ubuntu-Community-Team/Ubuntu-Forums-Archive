---
title: "bug installing koffice 2 beta 5"
date: 2009-01-30
forum: General Help
---

### Post by goneskiing on 2009-01-30
the installation fails on error with oxygen icon in another folder - has anyone got the new koffice to install correctly ?  ps: installed kde 4.2 and working fine.

---

### Post by Killerah on 2009-02-11
I had the same issue and I fixed it by running a series of commands that forced dpkg to overwrite the icons. It's kind of a sloppy hack, but it seems to have worked. 

I put in "sudo dpkg -i --force-overwrite /var/cache/apt/archives/koffice*" (without the quotes), and it came up with a list of packages that needed the same treatment on them. Like karbon-kde4 for example. So I ran through the same process with all the packages it listed I.E. "sudo dpkg -i --force-overwrite /var/cache/apt/archives/karbon*" and then ran the first command again and it installed OK.

The problem is that the koffice is buggy in it's current state, it seems like it'll be a great office suite once it's more stable. But from what I've seen it just crashes any time you try to load any larger documents. So I ended up just sticking with Open Office anyway.

---

### Post by rouge568 on 2009-03-07
This has been fixed if koffice beta6 and onwards. Beta 6 isn't in the repositories yet, however, so you'll have to wait until it is.
[https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/303405](https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/303405)

---

