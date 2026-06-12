---
title: "Backup Soulution"
date: 2008-02-11
forum: Desktop Environments
---

### Post by starknight on 2008-02-11
Hi i'm totally new to linux in general and need to backup a directory. I need it to be incremental mon-fri and full on sat. I looked into amanda a little bit but have no idea how to configure it to do what i want. Any recomndations to a GUI based backup or something that would do what i need, would be great. I am currently running

---

### Post by nemilar on 2008-02-11
I'm not sure that there's a GUI program available to do exactly what you want, although there are some decent backup GUIs available.  I personally use [http://www.techthrob.com/tech/timevault.php]("http://www.techthrob.com/tech/timevault.php") but Flyback is another good one.  Neither of them do quite what you want, though.

You may find it easier just to schedule a couple of CRON jobs with rsync and cp.  It'd probably take less time than researching and looking at other programs.

---

### Post by Giradman on 2008-02-11
Have you looked at the 'Simple Backup Config' in the System/Administration folder - I've just tried it once (fairly new to Ubuntu) - indeed, a 'simple' program but may provide what you need?  Will be interested in other responses & suggestions - good luck in finding what your need - :)

---

### Post by starknight on 2008-02-12
thanks for the input. I tried simple backup and it seems to work except it seems to mess up the file permissions. I might be wrong on this because i am very new to Linux in general.

---

