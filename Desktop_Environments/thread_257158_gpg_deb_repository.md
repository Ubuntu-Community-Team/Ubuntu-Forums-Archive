---
title: "gpg deb repository"
date: 2006-09-14
forum: Desktop Environments
---

### Post by jsgaarde on 2006-09-14
Hi.

I am trying to create my own deb repository. So far I have the the repository working but I am not using gpg. I am new to gpg and need some pointers to get started.

[OK] 1. I have the repository (unsigned, using dpkg-deb and dpkg-scanpackages)
[OK] 2. I have created a gpg key (gpg --gen-key)
[??] 3. What needs to be signed and how? When I look at the ubuntu repositories it I can see there is a Release/Release.gpg set under each distribution. This files appear to have been generated but how?
[??] 4. Do I need to sign anything else? I can see som .dsc files in some of the pool directories, but it doesn't seem like all packages have one.

Thanks
Jakob

---

