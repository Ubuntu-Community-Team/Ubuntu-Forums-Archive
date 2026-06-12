---
title: "gksudo caching password?"
date: 2004-12-08
forum: Desktop Environments
---

### Post by bazuka on 2004-12-08
Why is gksudo caching the password I enter? For instance, when running a root terminal. After the first time, it just lets me open shit. How can I get it to ask for a password EVERY time?

---

### Post by kamstrup on 2004-12-09
I would like to ask the same question... I think it must be related to sudo which does the same thing in a terminal. This is actually problematic you might "forget" that you have root privileges and issue devesdating commands.

---

### Post by WW on 2004-12-09
[http://ubuntuforums.org/showthread.php?t=5850](http://ubuntuforums.org/showthread.php?t=5850)

---

### Post by HungSquirrel on 2004-12-09
Short answer: edit /etc/sudoers and add a line similar to this, replacing 'username' with your user:

```
Defaults:username timestamp_timeout=0
```

Personally, I think immediate timeouts are a little over-paranoid.  I have mine set to three minutes.

---

