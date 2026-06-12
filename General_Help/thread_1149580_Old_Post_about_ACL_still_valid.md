---
title: "Old Post about ACL still valid?"
date: 2009-05-05
forum: General Help
---

### Post by randyklein99 on 2009-05-05
I ran across this [thread ]("http://ubuntuforums.org/showthread.php?t=145741")in the archives that laid out how share a directory with ACL.  Being 3 years old, I was wondering if it was still a valid solution or if anything has changed since then that would negate it.

---

### Post by randyklein99 on 2009-05-31
This is more of a personal post so I can recreate it later:

Here's how I used ACL to properly work with my Samba share:

On Samba server:
```

sudo setfacl -dR --set u:toshiba:rwx,g:toshiba:rwx,o::rx /home/shared

```

---

