---
title: "Syncing Evolution on two computers over bluetooth, wifi or lan?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Amon_Re on 2006-07-13
I was wondering if there's a way to sync evolution between 2 different computers,right now i'm just syncing my pda with both computers, but i was hoping there's another way.

---

### Post by markybob on 2006-07-13
Set up a cron job every minute on both computers and have rsync take care of copying over any changes via timestamps inside ~/.evolution

---

