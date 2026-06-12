---
title: "Why don't I have anything in /var/spool/mail?"
date: 2005-02-11
forum: Desktop Environments
---

### Post by rosslaird on 2005-02-11
/var/spool/mail is empty.
Shouldn't it at least have a directory called "root" and another for my main user?
And, assuming that I need to do something to get local mail working properly, what must I do?

/var/mail is empty too.

And, by the way, mail.err says this:

```
localhost postfix/local[18398]: fatal: open database /etc/aliases.db: No such file or directory
```

And mail.warn says this:

```
Feb 10 21:57:34 localhost postfix/master[6365]: warning: /usr/lib/postfix/local: bad command startup -- throttling
``` 


Ross

---

### Post by rosslaird on 2005-02-11
Google is my friend. For other folks with this problem, here's the fix:

newaliases

as root

---

