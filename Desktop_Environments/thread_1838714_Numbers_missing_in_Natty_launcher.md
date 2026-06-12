---
title: "Numbers missing in Natty launcher"
date: 2011-09-04
forum: Desktop Environments
---

### Post by sealevel on 2011-09-04
Something happened to my Natty launcher. After reboot, when pressing and holding the Windows key to display launcher, the short cut numbers won't appear. They don't work either. 
So, for instance pressing Windows+2 usually launches Firefox, but after a fresh boot it doesn't.
Strange thing is, the letters (like 's' for workspace and 'a' for applications) are displayed, and work. 

Then, if i go to Control Center, start 'launcher & menu's' and close it again, the numbers reappear on Launcher, and all works fine. Until next reboot.

Anyone? Thanks!

---

### Post by Leshrac on 2011-09-04
I don't know what could be causing this, it might be something simple like a misconfiguration.

Typing "unity --reset" without the quotes into a terminal should bring back the default configuration, this might fix your problem depending on what is causing it.

Edit: it looks like you might be experiencing this bug [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/768076](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/768076)

---

### Post by sealevel on 2011-09-06
Thx, and indeed, it's the same bug, and i noticed other recent threads on this issue. So much for my forum searching skills ... i'll just wait for the fix.

---

