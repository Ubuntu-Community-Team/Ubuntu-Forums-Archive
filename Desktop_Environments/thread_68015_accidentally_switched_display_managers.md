---
title: "accidentally switched display managers"
date: 2005-09-21
forum: Desktop Environments
---

### Post by RagingFuryBlack on 2005-09-21
Well,

I was updating to breezy, and switched my display manager from the default to the one that starts with a K.  It fails to load, and now I can only bootup in the shell.  How do i switch it back?

-Chris

---

### Post by Xian on 2005-09-21
I assume you mean KDM. Use this command:

```
$ sudo dpkg-reconfigure kdm
```

---

