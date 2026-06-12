---
title: "Can someone please help me with this error?"
date: 2009-05-13
forum: General Help
---

### Post by finalcut on 2009-05-13
I have no idea what this error means and every time I go to the update manager or the add/remove applications this error message appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to
correct the problem.
E:_cache->open() failed, please report.

Any help is greatly appreciated.

---

### Post by pro003 on 2009-05-13
this is a common thing, open terminal and type in:

# sudo dpkg --configure -a
  and then
# sudo apt-get update

---

