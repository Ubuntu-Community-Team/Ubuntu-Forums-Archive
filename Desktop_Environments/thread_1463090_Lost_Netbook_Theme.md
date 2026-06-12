---
title: "Lost Netbook Theme"
date: 2010-04-26
forum: Desktop Environments
---

### Post by rabbidous on 2010-04-26
Upon dist updating to 10.04 B2 (netbook) and later the release candidate, I lost my netbook theme in the process. I now have standard Ubutnu desktop (no big icons, no windows auto maximizing, lots of panels on the top and bottom in the way).

How do I get it back without reinstalling? I have tried deleting gnome config files, and this doesn't fix the problem.

Any ideas?

---

### Post by Megaptera on 2010-04-26
At log in just as you enter your p/w, look down to the right & see if when you click on 'sessions' you get netbook option.

---

### Post by rabbidous on 2010-04-26
That's easier than I thought and I wasn't looking in the right place... thanks.

---

### Post by Megaptera on 2010-04-26
You're welcome ... hope it works?

---

### Post by rabbidous on 2010-04-26
Works like a charm thank you.

---

### Post by Megaptera on 2010-04-27
:guitar:

---

### Post by rabbidous on 2010-04-27
It worked until I restart that is... now I am experiencing this bug (linking in case others have the same problem):

[https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all]("https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all")

Haven't had a chance to try the fixed desktop-switcher, but I am pretty sure that is the problem.

---

### Post by rabbidous on 2010-04-27
My panels disappeared on restart.

It is fixed (only for the current session) by running "metacity --replace" in a terminal.

---

