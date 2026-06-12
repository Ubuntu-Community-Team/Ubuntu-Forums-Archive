---
title: "Real Time Server Backup"
date: 2009-02-26
forum: General Help
---

### Post by bstras21 on 2009-02-26
Does anyone know of any open source programs that will allow me to provide real time backups? I have 2 ubuntu servers and I would like to have a one server feeding a real time back up to the other server. Or if anyone has any good ideas on how to do this I would appreciate it, thanks.

---

### Post by solwic on 2009-02-26
> **bstras21 said:**
> Does anyone know of any open source programs that will allow me to provide real time backups? I have 2 ubuntu servers and I would like to have a one server feeding a real time back up to the other server. Or if anyone has any good ideas on how to do this I would appreciate it, thanks.

Will rsync do this?  If you combined rsync and cron, you could do backups whenever you wanted...every minute, every hour, etc.  I do one backup a day, at 3:30pm.

Look into rsync.  And good luck.  :)

---

### Post by bstras21 on 2009-02-26
Well, I looked into that but the guy that wants this done wants it to be in real time. I found a couple programs but they are rather expensive.

---

