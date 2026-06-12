---
title: "Encrypted home directory keeps getting unmounted in 15.04"
date: 2015-07-08
forum: Desktop Environments
---

### Post by sean-hayes on 2015-07-08
It's happened 4 times today, I'll be in the middle of working, moving files around, and suddenly I get some sort of error saying the path doesn't exist. My home directory is replaced with "Access-Your-Private-Data.desktop" and "README.txt". I run `ecryptfs-mount-private` like the README says to and everything is fine again, until my home directory gets unmounted again.

---

### Post by simon-barron-19 on 2015-09-02
Pushing this up because I'm experiencing the same problem. It often happens when I connect to the 'Eduroam' wireless network in universities.

It might relate to this known bug [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1420236](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1420236)

---

