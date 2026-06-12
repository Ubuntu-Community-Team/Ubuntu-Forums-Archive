---
title: "What's the best way to back up /usr?"
date: 2009-03-19
forum: General Help
---

### Post by Neo_The_User on 2009-03-19
the topic says it all. the entire /usr directory in the RFS.

---

### Post by Beefeater on 2009-03-19
I would use rsync.

Something like

$ rsync -vrlptgoD /usr /backupfolder

---

### Post by Neo_The_User on 2009-03-19
ah ok. i was planning on backing it up in my home directory. good idea.

---

### Post by HermanAB on 2009-03-19
tar -zcvf usr.tgz /usr

Cheers,

Herman

---

