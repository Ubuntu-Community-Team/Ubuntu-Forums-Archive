---
title: "Need Help Building CDImages Locally"
date: 2023-08-22
forum: Development CD/DVD Image Testing
---

### Post by theofficialgman on 2023-08-22
I am trying to use ubuntu-cdimage [https://git.launchpad.net/ubuntu-cdimage](https://git.launchpad.net/ubuntu-cdimage) to create my own images/ISOs locally for architectures that are not natively supported by some of the official seed combinations [https://ubuntu-archive-team.ubuntu.com/seeds/](https://ubuntu-archive-team.ubuntu.com/seeds/) (for example, there are no kubuntu arm64 ISOs)

I can checkout the ubuntu-cdimage repo and run the python scripts locally. However on trying to target any of the seeds/arch combinations, I get an error along the lines of:
```

No live filesystem builder known for %s" % arch
```

I am not using launchpad to attempt to build these IOSs and need to do this locally. How can I generate IOSs that are the same as Ubuntu release ISOs with the provided seeds?

Before someone replies, these guides are NOT what I want [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) [https://wiki.ubuntu.com/ReleaseTeam/CDImageSetup](https://wiki.ubuntu.com/ReleaseTeam/CDImageSetup) . I need to build the ISO from scratch using the ACTUAL release seed files.

---

