---
title: "Gnome Terminal Startup Slow (11 Natty edition)"
date: 2011-08-16
forum: Desktop Environments
---

### Post by knappador on 2011-08-16
After several upgrades (from 8.xx) I noticed Gnome terminal took about 4 seconds to open an window and another 4 seconds to give me a prompt.

This is excruciating when blasting out CLI in dozens of terminals ssh'd into dozens of machines.  Tabs were no different.

Fix was:

**Comment out anything in ~/.bashrc that references xterm.  BOOM less than 1s total to prompt.**

If it's faster than I can get my mouse hand back to the keyboard to start blasting CLI, it's good enough :popcorn:

---

### Post by elliotbeken on 2011-08-16
Why does this make it faster ?

There must be a reason the code is there..

---

