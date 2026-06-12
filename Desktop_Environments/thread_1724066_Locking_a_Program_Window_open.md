---
title: "Locking a Program Window open"
date: 2011-04-07
forum: Desktop Environments
---

### Post by Bre Ntt on 2011-04-07
Is there a way to lock a program window open? 

I am taking an exam online, and I don't want to inadverantly close firefox during the exam. Is this possible?

---

### Post by Krytarik on 2011-04-07
What exactly do you need to prevent?

With Compiz' "Windows Rules" plugin it's possible to remove the close button from the titlebar of a specific window, by adding a respective window match to "Non closable windows", like this:
```
(class=Firefox & type=Normal)
```
But I don't believe that it's possible to *completely* prevent an app from closing.

Greetings.

---

