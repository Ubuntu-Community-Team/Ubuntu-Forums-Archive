---
title: "XFCE Session save question"
date: 2005-12-25
forum: Desktop Environments
---

### Post by NiceMarmot on 2005-12-25
I have 2 users on this comp, and I can't save XFCE as the default for one user. When I login, I get an error that says the default session can't be saved because home/.dmrc needs to be owned by user and have 644 permissions. I changed the permissions, and here is the ls -l output:

brian@Downstairs:~$ ls -l .dmrc
-rw-r--r--  1 brian brian 26 2005-12-25 17:13 .dmrc
brian@Downstairs:~$

I'm pretty sure that those permissions are correct. Am I missing something?
Brian is the user I can't save the session as.

---

