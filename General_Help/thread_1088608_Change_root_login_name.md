---
title: "Change root login name"
date: 2009-03-06
forum: General Help
---

### Post by mnnajem on 2009-03-06
can I change the root login name?
I have tried the following commands without success:
1. usermod -l newname  oldname
2. sudo usermod -l newname oldname

The following message was issued:
usermod: unable to lock password file

Also I tried:
3. opening \etc\shadow

but this was not possible as well: you do not have permission you are not the owner of this file

---

### Post by kellemes on 2009-03-06
There is no root-login with Ubuntu.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

