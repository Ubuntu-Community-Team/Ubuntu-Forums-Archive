---
title: "F-Spot crahses SQLite error"
date: 2008-05-11
forum: Desktop Environments
---

### Post by davedosch on 2008-05-11
F-Spot crashes on me on my Ubuntu desktop. 

ddosch@DavesDesktop:~$ f-spot
Starting new FSpot server

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

I saw some older reports of similar problems but this was supposed to be fixed in 8.04 LTS... any suggestions?

---

### Post by framirez on 2008-05-22
I have the very same problem, so please let me know if you found out what it was

---

### Post by jgarell on 2008-06-06
I had the same problems with f-spot crashing with sqllite errors.....after much digging I found that just deleting the ~/.gnome2/f-spot/photos.db fixed the problem.   

This wasnt' a big deal for me since I hadn't imported any photos yet.

---

