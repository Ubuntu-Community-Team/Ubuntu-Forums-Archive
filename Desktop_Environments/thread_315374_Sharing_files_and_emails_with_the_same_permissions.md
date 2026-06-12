---
title: "Sharing files and emails with the same permissions on the same machine"
date: 2006-12-09
forum: Desktop Environments
---

### Post by redactech on 2006-12-09
I've been googling a lot recently and I tried many things without a real answer.

I have two users who wants to share the same folder and email. I managed to make it work for files created manually (using a new group with the proper umask - both users belong to this new group) but when a user create a new file/folder with an application (thunderbird for instance), the other user cannot have access to those newly created files.

So I'm looking for an elegant way to do that as there's no question to chmod /chgrp every time there's a change in the shared directory. If possible this elegant way should be reproducible by newbies afraid of CLI

thanks for your help

---

### Post by UberGeekInc on 2006-12-09
You need the set group ID bit.  Check here:

  [http://ussg.iu.edu/usail/tasks/fileper/fileper.html](http://ussg.iu.edu/usail/tasks/fileper/fileper.html)

And, of course, `man chmod`.

---

