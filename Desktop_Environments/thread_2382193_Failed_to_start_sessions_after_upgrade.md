---
title: "Failed to start sessions after upgrade"
date: 2018-01-10
forum: Desktop Environments
---

### Post by malcmail on 2018-01-10
Decided to move from 16.04 to 17(something) using the GUI and upgrade. CAme back to it this morning with the keyboard not working but sorted that out.

Now when I go to log in it tells me it has failed to start session. Atthe console I tried to install ubuntu-desktop but it has unmet dependencies (ubuntu-session).

Tried to install ubuntu-session and it won't as it depends on gnome-session-bin (>=3.24.0-0ubuntu1 and <3.25).
Tried to install gnome-session-bin..... unmet dep this time is libgles2-mesa (>=7.8.1)
libgles2-mesa....... needs libglapi-mesa (=17.0.7-0ubuntu0.17.04.1 but 17.2.4-0ubuntu~16.04.2 is to be installed) [guessing this is the issue]
libglapi-mesa.... says it it as at newest at version 17.2.4-0ubuntu~16.04.2.

So what am I missing here and how do I sort it out?  Thanks in advance.

---

### Post by malcmail on 2018-01-10
Finally got it. Use aptitude to downgrade the libglapi package. In case anyone is looking later one

---

