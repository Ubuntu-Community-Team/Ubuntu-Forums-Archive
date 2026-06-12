---
title: "GDMFlexiServer No Lock"
date: 2005-11-06
forum: Desktop Environments
---

### Post by imnes on 2005-11-06
How can I configure ubuntu so that gdmflexiserver is run with the --no-lock option?  I've got a family computer with a few accounts that don't have passwords, everything is working great except the screen locking on user switch, I need to disable that because that dialog forces you to enter a password (which doesn't work on nopass accounts).

Where is gdmflexiserver started / where can I change it?

Nick

---

### Post by imnes on 2005-11-07
Found where gdmflexiserver is started, it's started with -sl options (which should mean start a new server and don't lock the current session), but my sessions are being locked.  Any ideas where to look next?

Nick

---

