---
title: "autostart app in twm"
date: 2008-05-29
forum: Desktop Environments
---

### Post by alzaf on 2008-05-29
Hi

What I am looking for is for xterm to automatically start after twm is loaded. Is this possible?

---

### Post by bingoUV on 2008-05-29
In the file ~/.xsession (create if not present), add the following 
```

xterm &

```

---

