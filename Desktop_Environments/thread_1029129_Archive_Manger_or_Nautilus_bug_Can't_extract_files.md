---
title: "Archive Manger or Nautilus bug? Can't extract files"
date: 2009-01-03
forum: Desktop Environments
---

### Post by Ux64 on 2009-01-03
There seems to be some problem with filename handling when ever filename includes # (hash mark).

If I try to extract file test#test.zip using archive managers direct right click link from nautilus it always fails. If I rename that same file to test-test.zip it works perfectly. So there has to be some kind of string handling bug there.

 - Thanks

---

### Post by jrusso2 on 2009-01-03
# is usually an illegal character for a file name.  I am not sure about for Linux how ever.

---

### Post by Ux64 on 2009-01-07
> **jrusso2 said:**
> # is usually an illegal character for a file name.  I am not sure about for Linux how ever.

Seems to be working fine, with everything else than Archive Manager.

---

### Post by Ux64 on 2009-04-14
It's seems that same problem exists with File Roller. I reported it..

[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/361131](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/361131)

---

