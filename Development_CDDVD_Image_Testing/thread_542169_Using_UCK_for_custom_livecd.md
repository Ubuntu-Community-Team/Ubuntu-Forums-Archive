---
title: "Using UCK for custom livecd"
date: 2007-09-03
forum: Development CD/DVD Image Testing
---

### Post by gb64 on 2007-09-03
Using UCK 2.0.0-beta4  on 7.04 desktop x86 ( building within VMware VM ).

Making livecd with no special selections just to see if all works.
All seems to work OK, builds livecd iso file. Testing in VM.

Problem 1:   No menu at all. Livecd appears to load fine, screen assumes usual brown background, but no menu system at all. Suggestions?

Problem 2:  Would like to add virtualbox 1.5.0 released today as a package to include in livecd build. How do we add a deb package from local area - where do I put the package within the building area and how do I tell UCK to then include it?  Note this means having some choice other than just an internet repository.

---

### Post by gb64 on 2007-09-09
Rebuilt, with help from another forum, and menu now shows up.

Since no reply here about UCK, used advice from elsewhere. Opened separate terminal and copied files to within the tmp chroot area, used dpkg -i and installed OK. Had never done any of this before.

UCK works great to build a new customized livecd of ubuntu.

---

### Post by troseph on 2008-12-22
Would you happen to have a link to the other forums? I am interested in what you had to do.

---

