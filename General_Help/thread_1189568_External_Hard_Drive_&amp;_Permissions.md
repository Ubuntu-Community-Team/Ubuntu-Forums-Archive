---
title: "External Hard Drive &amp; Permissions"
date: 2009-06-16
forum: General Help
---

### Post by hivemind on 2009-06-16
I have a laptop hard drive I have been planning on turning into an external hard drive for some time.

Today I wiped it and reformatted it with GPartEd, but there seems to be a problem with the permissions. It says that I cannot read or write to it because I am not root. I am, however, administrator and I don't know what to do to change the permissions.

Halp?

---

### Post by merlinus on 2009-06-16
```

gksu nautilus

```

This will give you root privileges, so be careful.  Navigate to the drive, right-click, select properties and then permissions.  You should be able to change them from there.

---

