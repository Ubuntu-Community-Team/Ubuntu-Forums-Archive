---
title: "mirror"
date: 2009-01-14
forum: Desktop Environments
---

### Post by alisafeen1 on 2009-01-14
How can I add a new ubuntu mirror to my 'sources.list' file?

---

### Post by lukjad on 2009-01-14
Go to the terminal and type
```
/etc/apt/
```

Then type:

```
gksudo gedit sources.list
```

Go to the bottom of the page and add the mirror.

I think that is what you want. Also, be careful which repositories you add. Make sure they are from trusted sources.

---

