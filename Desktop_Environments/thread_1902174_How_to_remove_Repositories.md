---
title: "How to remove Repositories"
date: 2011-12-30
forum: Desktop Environments
---

### Post by jgray152 on 2011-12-30
I installed a repository only to have trouble getting it to work. Now im getting errors during updates and would like to get rid of it.

I need Ubuntu for Dummies or something haha.

So how do I get rid of "Handbrake" so it can be removed from updating.

W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by wyliecoyoteuk on 2011-12-30
open synaptic package manager, click on settings>repositories>other software tab.
highlight the handbrake repos and click remove.

---

### Post by JohnAStebbins on 2011-12-30
> **jgray152 said:**
> I installed a repository only to have trouble getting it to work. Now im getting errors during updates and would like to get rid of it.

I need Ubuntu for Dummies or something haha.

So how do I get rid of "Handbrake" so it can be removed from updating.

W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
If you want to use HandBrake on Oneiric, you need to use the snapshots repository instead of the releases repository.  The old 0.9.5 release does not build on Oneiric, so there is no package for Oneiric in the releases repo.

[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

