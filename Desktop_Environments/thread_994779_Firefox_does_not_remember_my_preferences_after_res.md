---
title: "Firefox does not remember my preferences after restart"
date: 2008-11-27
forum: Desktop Environments
---

### Post by jis on 2008-11-27
This is with ubuntu 8.10 , Firefox 3.0.4. The problem started once I tried running "sudo firefox" once. It works differently from "gksu firefox" (even after authentication) for some reason that I don't know. Anyway, Firefox can't remember my preferences even if I modify them as normal user and then restart as normal user.

---

### Post by jis on 2008-11-27
It is fixed after running this in command line; replace username by your username:
```

cd ~/.mozilla/firefox
sudo chown -R username:username *

```
(It should actually change the owner and the group of file named "prefs.js" only).

---

