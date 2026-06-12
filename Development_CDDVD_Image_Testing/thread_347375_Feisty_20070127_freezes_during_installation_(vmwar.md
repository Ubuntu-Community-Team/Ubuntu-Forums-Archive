---
title: "Feisty 20070127 freezes during installation (vmware)"
date: 2007-01-27
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-27
In case you felt the weekend is a nice time for testing daily isos, I have to disappoint you a bit: today's build (Jan 27) of the desktop amd64 iso has the same old herd2+ symptoms during installation - it can create partitions but cannot format them - so it freezes. Unfortunately, since the desktop versions force formatting of the sda1 ( / ) partition, there is no workaround.

This is an old bug that reappeared just today - all this week's builds were OK.

I am testing feisty in vmware, but I expect the same behaviour in x86 and amd64 kubuntu, xubuntu, dvd etc. The alternate cd might be ok (but only when installing on new hard disk).

I will make comments in the appropriate Launchpad bug threads.

UPDATE: fixed in 20070128 desktop amd64

---

