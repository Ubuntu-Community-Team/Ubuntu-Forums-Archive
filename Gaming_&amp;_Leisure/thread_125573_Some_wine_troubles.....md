---
title: "Some wine troubles...."
date: 2006-02-04
forum: Gaming &amp; Leisure
---

### Post by Wallakoala on 2006-02-04
So I was changing some options in winecfg....I changed a couple of things:
I made it so the app is not handled by the window manager(probably a bad idea) and I also changed it so it did not emulate a virtual desktop. Now the problem is, I can't start any apps with wine at all. For example, when I want to run winecfg, I get the following error:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```

Can anyone help?

---

### Post by zodder on 2006-02-04
Me too. :(

---

### Post by Wallakoala on 2006-02-04
[QUOTE=zodder]Me too. :([/QUOTE]
Well I fixed it....I just deleted my whole .wine directory and then ran wine again to recreate it.

---

### Post by zodder on 2006-02-14
Same here. I recompiled it and it installed fine afterwards. Go figure.

---

