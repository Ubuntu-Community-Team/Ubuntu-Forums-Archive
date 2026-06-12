---
title: "Upgrade pkg from unstable Debian archive?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by osmiroid on 2005-11-03
The version of Sooperlooper available in the Ubuntu archives is ancient.  A current version is available in Debian unstable.  How can I apt-get it without messing up my sources.list?

TIA to anyone who can help....

---

### Post by poofyhairguy on 2005-11-03
That was the wrong forum for questions. Your answer is that such an action is not recommended and it might break things. If you must do it than download the single package and install it with the 

> sudo dpkg -i pacakgename.deb

command. That might nto work, but its far less dangerous than putting the Sid line in your sources.list and trying to apt-get it. Doing such a thing can and probably will break your system.

---

