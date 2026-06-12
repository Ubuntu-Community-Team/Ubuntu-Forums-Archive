---
title: "apt-get can't find update for vmware-player-kernel"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Pawel Stolowski on 2006-07-30
I've a strange problem with apt-get. I've been using vmware-player deb from ubuntu repository as well as vmware-player-kernel packages for some time. The problem is apt-get doesn't see updates for vmware-player-kernel package for latest kernel 2.6.15-26. I checked manually the repository ([http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/), it's in multiverse) and IT IS there. But apt-get update && apt-get upgrade doesn't detect the updated package (neither it is listed in synaptic). I think the entry in my sources.list is ok:

deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

Any idea on what may be wrong? I tried [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) as well as [http://archive.ubuntu.com](http://archive.ubuntu.com) but no luck.

---

