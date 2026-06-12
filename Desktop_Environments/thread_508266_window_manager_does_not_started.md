---
title: "window manager does not started"
date: 2007-07-24
forum: Desktop Environments
---

### Post by jimhce on 2007-07-24
It was working fine yesterday, but this  morning, the window manager was not started, all window frames stuck. How to fix it? Is it a bug on 7.04?

Jim

---

### Post by zanglang on 2007-07-24
Seems fine here, and no updates were released today... Might be a random crash. Does re-logging in or rebooting solve it?

---

### Post by jimhce on 2007-07-25
Restart does not fix it. I've deleted all .gnome* directories, but the window manager is still missing.  (I have to manually start the window manager :-()

---

### Post by pfiglioli on 2007-07-26
i have the same problem. i just installed Ubuntu, the window manager worked until i installed the recommended upgrades. can you tell me how to manually start the window manager until we know how to fix this problem?

---

### Post by jimhce on 2007-07-26
Just learned from other people, please try following, it should fix the problem.

using the session manager (system>preferences>sessions), put metacity as a new item to startup using the following:

Name: give it whatever name you want
command: metacity --replace

---

