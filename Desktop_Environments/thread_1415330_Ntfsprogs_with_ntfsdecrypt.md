---
title: "Ntfsprogs with ntfsdecrypt?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by allaboutsam on 2010-02-24
Anyone know if there is a deb of ntfsprogs for 8.10 *including* ntfsdecrypt, which is excluded from the package in the main repository? (Anyone know why it is excluded? Does it break something?)

Thanks,
allaboutsam

---

### Post by KenSharp on 2010-06-16
ntfsdecrypt is not included in any packages.

Probably because when you compile from source, despite adding --enable-crypto to configure, it ignores you and doesn't bother building.  I doubt a working binary exists anywhere.

---

