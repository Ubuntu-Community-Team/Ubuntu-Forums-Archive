---
title: "Ubuntu Herd 2  - I386 Alternative CD"
date: 2007-01-11
forum: Development CD/DVD Image Testing
---

### Post by spd106 on 2007-01-11
Test case type: Ubuntu Herd 2 -- I386 Alternative CD, manual partitioning
Image ID: 20070111.3
Date of testing: 2007-01-12
md5sum confirmed: Yes
Pass/Fail: PASS
Bugs identified: [#76294]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/76294") and [#76641]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/76641") 

Bonus: Hibernate now works from the shutdown menu.
Regressions: Atheros wifi cards don't work on kernel 2.6.20 yet, this causes the card to be unrecognised by installer and a kernel oops after installing restricted-modules.

Long standing issues: No software suspend, sound errors w/ external USB drive and no poweroff during shutdown. See laptop page at [http://wiki.ubuntu.com/LaptopTestingTeam/Kapok3300C](http://wiki.ubuntu.com/LaptopTestingTeam/Kapok3300C)

---

