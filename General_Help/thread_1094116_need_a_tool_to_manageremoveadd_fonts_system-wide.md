---
title: "need a tool to manage/remove/add fonts system-wide"
date: 2009-03-12
forum: General Help
---

### Post by offchance on 2009-03-12
In Ubuntu my fonts are spread far and wide. Some are available to OpenOffice that are not available to Gimp and others. Some are specific to certain applications (like Java). 

What I want is a way to consolidate all these fonts into one folder so that I can see what's out there, share them equally among all my applications, and remove the ones I do not need.

Any suggestions?

---

### Post by oldos2er on 2009-03-12
Copy or move them into /usr/share/fonts , then run sudo fc-cache -f -v

---

