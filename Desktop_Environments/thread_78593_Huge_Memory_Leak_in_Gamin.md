---
title: "Huge Memory Leak in Gamin"
date: 2005-10-18
forum: Desktop Environments
---

### Post by talkingwires on 2005-10-18
There is a [known memory leak]("https://bugzilla.ubuntu.com/show_bug.cgi?id=13449") in gamin that can cause it to consume 1.5Gb (or more) of memory, effectively bringing the system to a crawl. The Gnome developers have  [issued a patch]("http://bugzilla.gnome.org/show_bug.cgi?id=313846"), but the Ubuntu developers decided not to include it in Breezy.

I know that the bug is considered fairly rare, but it is serious as it brings the entires system down. Why did the developers decline to include the patch?

---

### Post by talkingwires on 2005-10-18
Hrm, some reading [answered my own question](https://bugzilla.ubuntu.com/show_bug.cgi?id=13449#c8):> This bug is supposed to be fixed with 0.1.6 ... version which already has a
"Large revamp of the inotify back-end" according to the NEWS file, so something
we probably don't want to push just before a new stable. fcrozat backported the
leak fix to 0.1.5 for mandriva but rolled it back then since it seems to create
some crash with it ...So, instead of delaying Ubuntu to ship a stable product, the developers decided to choose between a show-stopping crash and a system-grinding memory leak. Um, nice one, guys... :(

---

