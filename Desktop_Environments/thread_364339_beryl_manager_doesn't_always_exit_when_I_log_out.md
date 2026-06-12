---
title: "beryl manager doesn't always exit when I log out?"
date: 2007-02-18
forum: Desktop Environments
---

### Post by CaptSaltyJack on 2007-02-18
I noticed after logging out, that the beryl-manager process is sometimes still running.  Yet other times it closes properly.  How do I ensure it always quits??

It runs via a script, beryl-startup, in my .kde/Autostart folder:

```
#!/bin/sh
sleep 7; beryl-manager
```

Any ideas?

---

