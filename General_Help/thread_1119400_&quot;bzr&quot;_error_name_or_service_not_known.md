---
title: "&quot;bzr&quot; error: name or service not known"
date: 2009-04-07
forum: General Help
---

### Post by xiaoqi on 2009-04-07
On website: [https://wiki.ubuntu.com/DocumentationTeam/Translation](https://wiki.ubuntu.com/DocumentationTeam/Translation)

Want to involve in some translation tasks, but the 2nd command got below error, please help, thanks.

Error Message in Terminal --
==========
xiaoqi@xiaoqi-ubuntu9:~$ sudo bzr checkout --lightweight lp:ubuntu-doc/intrepid ubuntu-docs-intrepid
bzr: ERROR: [Errno -2] Name or service not known
==========

---

### Post by jdong on 2009-04-07
That typically means you cannot access the Launchpad Bazaar server. Try **ping bazaar.launchpad.net** and see if you can resolve it to 91.189.90.11

---

