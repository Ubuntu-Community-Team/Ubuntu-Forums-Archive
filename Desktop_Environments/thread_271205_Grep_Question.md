---
title: "Grep Question"
date: 2006-10-04
forum: Desktop Environments
---

### Post by crypticstatic on 2006-10-04
I'm trying to find a specific user name in a directory that contains a lot of different scripts that may contain this specific user name in several of them.

Is there a syntax I can use with grep to find out in which files contains this user name?

Thanks in advance.

---

### Post by mitch.c on 2006-10-04
> **crypticstatic said:**
> I'm trying to find a specific user name in a directory that contains a lot of different scripts that may contain this specific user name in several of them.

Is there a syntax I can use with grep to find out in which files contains this user name?

Thanks in advance.
Try this:
```
# Search for "username"; descend into subfolders ("-r")
grep -ir "username" /path/to/directory/
```

---

