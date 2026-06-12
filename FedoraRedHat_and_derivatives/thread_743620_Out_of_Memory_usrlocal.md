---
title: "Out of Memory /usr/local"
date: 2008-04-02
forum: Fedora/RedHat and derivatives
---

### Post by Auston on 2008-04-02
Ive just run out of memory on the /usr/local folder of my redhat linux install, /usr indicates there are 4.5 Gigs free but the usr/local folder only contains 80.8 megs so I am at a loss as to why usr/local also indicates there is 0 space available. I determined the space available by checking the properties of each folder. Can anyone point me in the right direction to understand how this is possible and how to reclaim the space I imagine exists but is inaccessible for some reason

I tried running that fsck command but got the following so aborted

[root@tdspace root]# fsck
fsck 1.32 (09-Nov-2002)
e2fsck 1.32 (09-Nov-2002)
/dev/sda3 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

[Ubuntu Masters]("http://www.linux-archive.org/ubuntu-masters-universe/")

---

