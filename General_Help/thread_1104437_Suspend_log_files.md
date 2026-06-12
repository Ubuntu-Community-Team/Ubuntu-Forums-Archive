---
title: "Suspend log files?"
date: 2009-03-23
forum: General Help
---

### Post by lems on 2009-03-23
Where are the log files stored when you suspend your computer? Whenever I resume from suspend, my computer freezes up on me at the login screen. I haven't found a fix yet on the forums so I want to take a look at the logs myself.

---

### Post by kanikilu on 2009-03-23
All the logs should be in /var/log/ - as for which one to look through, I generally check Xorg.0.log, syslog, messages and dmesg if I don't already know which one applies to the problem.

---

### Post by Dr Small on 2009-03-23
You can check out both of thees logs:
```
/var/log/syslog
/var/log/messages
```

---

### Post by jordilin on 2009-03-23
take a look at /var/log/messages and see what is going on.

---

