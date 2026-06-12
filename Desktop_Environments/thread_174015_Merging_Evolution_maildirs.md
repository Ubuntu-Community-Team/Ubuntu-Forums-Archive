---
title: "Merging Evolution maildirs"
date: 2006-05-11
forum: Desktop Environments
---

### Post by mikl on 2006-05-11
Due to a mess-up at some point, I have two Evolution maildirs, one containing all my old mail, and one containing all my new mail. Logically, I'm not interested in loosing either - so what do I do? How can I merge these maildirs, without breaking stuff?

---

### Post by dcstar on 2006-05-12
[QUOTE=mikl]Due to a mess-up at some point, I have two Evolution maildirs, one containing all my old mail, and one containing all my new mail. Logically, I'm not interested in loosing either - so what do I do? How can I merge these maildirs, without breaking stuff?[/QUOTE]
In theory, you should be able to create a new .sbd subdirectory in your (hidden) .evolution/mail/local/Inbox.sbd directory and copy all the old .evolution/mail/local/ stuff there.

Restarting Evolution should give you access to the old stuff in that directory.

---

