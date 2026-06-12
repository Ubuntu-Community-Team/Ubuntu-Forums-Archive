---
title: "Realplayer Stopped Working"
date: 2005-07-28
forum: Desktop Environments
---

### Post by delirium on 2005-07-28
Yesterday, Realplayer 10 worked like a charm, and now, it doesn't work at all.  The program doesn't even start.  Someone help please.

---

### Post by strikeforce on 2005-07-28
Any errors?  Have a look at /var/log

---

### Post by delirium on 2005-07-29
[QUOTE=strikeforce]Any errors?  Have a look at /var/log[/QUOTE]
 What should I be looking for?  realplayer.log???

---

### Post by titus1950 on 2005-07-29
[QUOTE=delirium]What should I be looking for?  realplayer.log???[/QUOTE]


Just in case,try >   System....preferences....Sound...."uncheck" Enable start server startup

---

### Post by delirium on 2005-07-31
[QUOTE=titus1950]Just in case,try >   System....preferences....Sound...."uncheck" Enable start server startup[/QUOTE]
 Thanks, I did some more searching and I think I fixed the problem by forcing Real to use ALSA instead of its default OSS.

---

### Post by aashay on 2008-01-13
my realplayer just started hanging on startup. How did you solve the problem?

---

