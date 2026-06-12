---
title: "Absolutely Clueless &gt;.&lt;"
date: 2009-03-27
forum: General Help
---

### Post by amy24 on 2009-03-27
Whenever I try to update or Add/Remove anything this appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and doesn't let me do anything. I've tried running what it says but it doesn't seem to work, unless I'm doing something wrong??

Help :(

Thanks in advance

Amy x

---

### Post by 3Miro on 2009-03-27
I think you have to do it as root, i.e.

> 
sudo 'dpkg --configure -a


You are supposed to type this in the terminal (Apps -> Accessories -> Terminal).

---

