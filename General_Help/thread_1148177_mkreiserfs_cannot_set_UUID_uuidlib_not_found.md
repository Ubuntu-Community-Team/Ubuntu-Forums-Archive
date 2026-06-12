---
title: "mkreiserfs cannot set UUID: uuidlib not found"
date: 2009-05-04
forum: General Help
---

### Post by tkanter on 2009-05-04
mkreiserfs did not set an uuid for a new volume. reiserfstune was unable to locate uuidlib. The package manager mentions uuidlib1 instead of uuidlib.

$ sudo reiserfstune --uuid <someuuid> /dev/vgVGRP/lvLVOL
reiserfstune: Cannot set the UUID, uuidlib was not found by configure.

One alternative is to set the UUID via parted from a live CD.
Is there any other way to set the UUID than using reiserfstune?
Will reiserfsprogs be updated to point at uuidlib1? 
Can we rely on reiserfsprogs in Ubuntu or is it time to move on to another file system?

PS My system is an updated Ubuntu 8.04 LTS with an 2.6.24-23 kernel.

--theo

---

