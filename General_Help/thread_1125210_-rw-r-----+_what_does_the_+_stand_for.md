---
title: "-rw-r-----+ what does the + stand for?"
date: 2009-04-14
forum: General Help
---

### Post by conehead77 on 2009-04-14
On the computer of my university i have some files (.svn-access and .svn-passwd) that are listed like this:
```

-rw-r-----+  1 *** students     128 2009-01-14 16:57 .svn-access
-rw-r-----+  1 *** students       0 2008-08-25 15:33 .svn-passwd
-rw-------   1 *** students       8 2008-06-03 11:59 test

```
What does the + mean? I never saw it before.

---

### Post by kpatz on 2009-04-14
It means the file has an extended access control list (ACL) applied to it.  Long story short, an ACL allows more than one set of permissions on a file/directory.

**man getfacl**
**man setfacl**
**man acl**

for more information...

---

### Post by sedawk on 2009-04-14
The unix system used another (advanced) mechanism to manage permissions,
e.g. "ACLs" (Access Control Lists). The plus symbol indicates there
are additional permission defined somewhere else (e.g. in the ACLs).

---

### Post by conehead77 on 2009-04-14
Ah, i see. Thanks a lot!

---

