---
title: "what apps are auto updated through dapper repo's ?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by syxbit on 2006-07-22
is it true that only firefox gets updated and for every other update (i.e. open office etc..) we either have to compile it ourselves, or wait for the next ubuntu release to have it incorporated ?

---

### Post by SimonJW on 2006-07-22
The usual method of upgrading Ubuntu (and most other distros) is that no software gets upgrade, including firefox, until the next ubuntu release. THe only updates once a release is brought out of beta and into final are for security reasons. Ocassionally this rule is bypassed, and a new updated version of a software is supplied, but you can never count on this happening.

If you are interested in the latest, but don't want to run Edgy (as it is nowhere NEAR to being stable, and WILL break a few times before it is released) you can check Backports. There is no guarentee a program will make it into Backports though. Witness the way Firefox 1.5 never made it to Breezy, even through backports, although it was out for several months of Breezy's existance.

---

### Post by syxbit on 2006-07-22
> **SimonJW said:**
> The usual method of upgrading Ubuntu (and most other distros) is that no software gets upgrade, including firefox, until the next ubuntu release. THe only updates once a release is brought out of beta and into final are for security reasons. Ocassionally this rule is bypassed, and a new updated version of a software is supplied, but you can never count on this happening.

If you are interested in the latest, but don't want to run Edgy (as it is nowhere NEAR to being stable, and WILL break a few times before it is released) you can check Backports. There is no guarentee a program will make it into Backports though. Witness the way Firefox 1.5 never made it to Breezy, even through backports, although it was out for several months of Breezy's existance.

so backports is basically that program compiled for a later unstable version of ubuntu (in this case edgy) ?

---

### Post by SimonJW on 2006-07-22
Backports is another repostiory which you can add, where programs from Edgy are tweaked to work under Dapper. Stability is not guaranteed. You can turn on backports by adding
```

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```
to your /etc/apt/sources.list file.

Other than that, you will have to compile the programs yourself, or find unofficial debs or repo's to keep up-to-date. For example, I know of (but can't remember at the mo) repos for the latest versions of Wine, Amarok and KDE are around somewhere.

Good luck!

---

