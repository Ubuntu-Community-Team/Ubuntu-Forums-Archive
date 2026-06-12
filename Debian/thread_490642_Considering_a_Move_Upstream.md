---
title: "Considering a Move Upstream"
date: 2007-07-02
forum: Debian
---

### Post by BarfBag on 2007-07-02
I'm looking for something more bleeding edge then Ubuntu, but stable at the same time.  I looked into Arch, and I really liked it.  Pacman just isn't as good as ol' apt-get, though.  Debian Stable is definitely ruled out.  I'm assuming that Ubuntu follows a similar format with their releases (meaning - each Ubuntu release has, for the most part, the same packages in it's repos the entire cycle)?  Is Debian testing any more bleeding edge?

---

### Post by Adamant1988 on 2007-07-02
IIRC Ubuntu is actually based on sid, so Debian Testing would probably be behind  Ubuntu.

---

### Post by BarfBag on 2007-07-02
> **Adamant1988 said:**
> IIRC Ubuntu is actually based on sid, so Debian Testing would probably be behind  Ubuntu.

o_O  How is this possible?  Isn't sid as bleeding edge as possible?

---

### Post by machoo02 on 2007-07-02
Sid is the development version, where all of the packages first enter the Debian system.  After they've been there for a while, and no major bugs have cropped up, packages will be moved into testing.  Eventually, once there are relatively few impending bugs, testing is frozen and becomes the next stable release.

Ubuntu development basically takes a snapshot of the sid repositories every six months and uses that as the basis for the next release.

If you are looking for something that is stable and bleeding edge (although that's almost an oxymoron), you could check out sidux, which has a goal of making sid a stable desktop distribution.

---

### Post by tommcd on 2007-07-03
Try Zenwalk.  [http://zenwalk.org/](http://zenwalk.org/) It is more bleeding edge than Ubuntu, and is rock solid stable. Their netpkg package manager is pretty good also, but not quite as good as APT imo. Zenwalk does not have thousands of packages in their repos like debian/ubuntu, but they have a program for just about everything you would ever need to do, and more are being added all the time. Compiling from source is probably easier in zenwalk as well, but I have limited experience with that.

---

