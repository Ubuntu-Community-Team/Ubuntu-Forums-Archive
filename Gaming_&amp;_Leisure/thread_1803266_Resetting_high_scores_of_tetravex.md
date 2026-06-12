---
title: "Resetting high scores of tetravex"
date: 2011-07-13
forum: Gaming &amp; Leisure
---

### Post by espritdumal on 2011-07-13
:confused:
Does someone know how to reset the scores in the tetravex game?
It contains some names I do not need to see on my PC anymore.

Thanks for your help!

---

### Post by realzippy on 2011-07-13
Open terminal,run:

```
gksudo gedit /var/games/gnotravex.3x3.scores
```

(If playing eg 4x4 you have to change the command of course to eg:
*gksudo gedit /var/games/gnotravex.4x4.scores*)

Delete everything in the file (Or change the names...  ;-)   )
,close and save empty file.
Done.

---

### Post by espritdumal on 2011-07-14
Thanks a lot!

---

### Post by realzippy on 2011-07-14
You are welcome.
please set thread as "solved"  (Threadtools)....

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

