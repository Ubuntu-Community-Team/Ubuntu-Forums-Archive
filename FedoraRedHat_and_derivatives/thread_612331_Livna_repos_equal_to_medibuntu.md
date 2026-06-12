---
title: "Livna repos equal to medibuntu?"
date: 2007-11-13
forum: Fedora/RedHat and derivatives
---

### Post by 67GTA on 2007-11-13
I tried Fedora 6 when it came out and quickly got rid of it. I was used to the Debian way of doing things. I admit, I didn't do much reading, or looking for answers. I was thinking of trying Fedora 8. I was reading about the Livna repos, and couldn't find what packages were in it except for video drivers. What about flash, java, mp3, libdvdcss, etc. Is it the Fedora equivalent to Ubuntu's Medibuntu repo?

---

### Post by igknighted on 2007-11-13
> **67GTA said:**
> I tried Fedora 6 when it came out and quickly got rid of it. I was used to the Debian way of doing things. I admit, I didn't do much reading, or looking for answers. I was thinking of trying Fedora 8. I was reading about the Livna repos, and couldn't find what packages were in it except for video drivers. What about flash, java, mp3, libdvdcss, etc. Is it the Fedora equivalent to Ubuntu's Medibuntu repo?

Umm, yes and no.  It is more like Fedora's non-free repo.  The "official distro" does not package any non-free software, so stuff like video drivers and madwifi are there, as are things like libdvdcss and the patent-encumbered packages.  Adobe has a special repository set up to add to YUM so that you can stay current with the latest flash player as well.

There are also other options than Livna.  There is ATRPMs, FreshRPMs, and several more.  It is usually ok to install a package or two from more than one, but never have them enabled at the same time, as package conflicts will arise.  There is a project merging the major ones into one repository called rpm-fusion, but that is not ready yet.

Personally, I use livna.  I think it is the best option for packages that fedora does not support itself (as well as a few here and there, like one for fusion-icon and another to keep the latest AWN... ubuntu has these little personal ones around as well)

---

